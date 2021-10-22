# Read: 19 - Spring and Sockets

## Real time messaging with websockets

WebSocket is a thin, lightweight layer above TCP. This makes it suitable for using “subprotocols” to embed messages. In this read, we use STOMP messaging with Spring to create an interactive web application. STOMP is a subprotocol operating on top of the lower-level WebSocket.

![WebSockets Advanced](https://geekhmer.github.io/images/websocket_processing.png)

### Get started

- From https://start.spring.io select gradle and add Websocket dependency then click on generate. or
  Download and unzip the source repository, or clone it using Git: git clone https://github.com/spring-guides/gs-messaging-stomp-websocket.git

- cd into gs-messaging-stomp-websocket/initial

- Jump ahead to Create a Resource Representation Class.

- When you finish, you can check your results against the code in gs-messaging-stomp-websocket/complete.

### Create a Resource Representation Class

**Create The Model that carries the name**

```
package com.example.messagingstompwebsocket;

public class HelloMessage {

  private String name;

  public HelloMessage() {
  }

  public HelloMessage(String name) {
    this.name = name;
  }

  public String getName() {
    return name;
  }

  public void setName(String name) {
    this.name = name;
  }
}
```

**Create The Model that carries the name**

```
package com.example.messagingstompwebsocket;

public class Greeting {

  private String content;

  public Greeting() {
  }

  public Greeting(String content) {
    this.content = content;
  }

  public String getContent() {
    return content;
  }

}
```

**Create a Message-handling Controller**

```
package com.example.messagingstompwebsocket;

import org.springframework.messaging.handler.annotation.MessageMapping;
import org.springframework.messaging.handler.annotation.SendTo;
import org.springframework.stereotype.Controller;
import org.springframework.web.util.HtmlUtils;

@Controller
public class GreetingController {


  @MessageMapping("/hello")
  @SendTo("/topic/greetings")
  public Greeting greeting(HelloMessage message) throws Exception {
    Thread.sleep(1000); // simulated delay
    return new Greeting("Hello, " + HtmlUtils.htmlEscape(message.getName()) + "!");
  }

}
```

The @MessageMapping annotation ensures that, if a message is sent to the /hello destination, the greeting() method is called.

The payload of the message is bound to a HelloMessage object, which is passed into greeting().
After the one-second delay, the greeting() method creates a Greeting object and returns it. The return value is broadcast to all subscribers of /topic/greetings, as specified in the @SendTo annotation

**Configure Spring for STOMP messaging**

```
package com.example.messagingstompwebsocket;

import org.springframework.context.annotation.Configuration;
import org.springframework.messaging.simp.config.MessageBrokerRegistry;
import org.springframework.web.socket.config.annotation.EnableWebSocketMessageBroker;
import org.springframework.web.socket.config.annotation.StompEndpointRegistry;
import org.springframework.web.socket.config.annotation.WebSocketMessageBrokerConfigurer;

@Configuration
@EnableWebSocketMessageBroker
public class WebSocketConfig implements WebSocketMessageBrokerConfigurer {

  @Override
  public void configureMessageBroker(MessageBrokerRegistry config) {
    config.enableSimpleBroker("/topic");
    config.setApplicationDestinationPrefixes("/app");
  }

  @Override
  public void registerStompEndpoints(StompEndpointRegistry registry) {
    registry.addEndpoint("/gs-guide-websocket").withSockJS();
  }

}
```

- WebSocketConfig is annotated with @Configuration to indicate that it is a Spring configuration class. It is also annotated with @EnableWebSocketMessageBroker. As its name suggests, @EnableWebSocketMessageBroker enables WebSocket message handling, backed by a message broker.

- The configureMessageBroker() method implements the default method in WebSocketMessageBrokerConfigurer to configure the message broker. It starts by calling enableSimpleBroker() to enable a simple memory-based message broker to carry the greeting messages back to the client on destinations prefixed with /topic. It also designates the /app prefix for messages that are bound for methods annotated with @MessageMapping. This prefix will be used to define all the message mappings. For example, /app/hello is the endpoint that the GreetingController.greeting() method is mapped to handle.

-The registerStompEndpoints() method registers the /gs-guide-websocket endpoint, enabling SockJS fallback options so that alternate transports can be used if WebSocket is not available. The SockJS client will attempt to connect to /gs-guide-websocket and use the best available transport (websocket, xhr-streaming, xhr-polling, and so on).

**ClientSide**

![WebSockets connection](https://1.bp.blogspot.com/-_AbYGt3Q3b0/WIRh2WhkmKI/AAAAAAAAQLo/f662nOh2dnoeVHMSi_BpLerv8OicOQ6SwCLcB/s1600/websocket8.png)

This HTML file imports the SockJS and STOMP javascript libraries that will be used to communicate with our server through STOMP over websocket. We also import app.js, which contains the logic of our client application. The following listing (from src/main/resources/static/app.js) shows that file:

```
var stompClient = null;

function setConnected(connected) {
    $("#connect").prop("disabled", connected);
    $("#disconnect").prop("disabled", !connected);
    if (connected) {
        $("#conversation").show();
    }
    else {
        $("#conversation").hide();
    }
    $("#greetings").html("");
}

function connect() {
    var socket = new SockJS('/gs-guide-websocket');
    stompClient = Stomp.over(socket);
    stompClient.connect({}, function (frame) {
        setConnected(true);
        console.log('Connected: ' + frame);
        stompClient.subscribe('/topic/greetings', function (greeting) {
            showGreeting(JSON.parse(greeting.body).content);
        });
    });
}

function disconnect() {
    if (stompClient !== null) {
        stompClient.disconnect();
    }
    setConnected(false);
    console.log("Disconnected");
}

function sendName() {
    stompClient.send("/app/hello", {}, JSON.stringify({'name': $("#name").val()}));
}

function showGreeting(message) {
    $("#greetings").append("<tr><td>" + message + "</td></tr>");
}

$(function () {
    $("form").on('submit', function (e) {
        e.preventDefault();
    });
    $( "#connect" ).click(function() { connect(); });
    $( "#disconnect" ).click(function() { disconnect(); });
    $( "#send" ).click(function() { sendName(); });
});
```

The main pieces of this JavaScript file to understand are the connect() and sendName() functions.

The connect() function uses SockJS and stomp.js to open a connection to /gs-guide-websocket, which is where our SockJS server waits for connections. Upon a successful connection, the client subscribes to the /topic/greetings destination, where the server will publish greeting messages. When a greeting is received on that destination, it will append a paragraph element to the DOM to display the greeting message.

The sendName() function retrieves the name entered by the user and uses the STOMP client to send it to the /app/hello destination (where GreetingController.greeting() will receive it).

The main.css can be omitted if you like, or you can create an empty one, just so the <link> can be resolved.

**Build an executable JAR**
If you use Gradle, you can run the application by using ./gradlew bootRun. Alternatively, you can build the JAR file by using ./gradlew build and then run the JAR file, as follows:

java -jar build/libs/gs-messaging-stomp-websocket-0.1.0.jar

**Test the service**

Now that the service is running, point your browser at http://localhost:8080 and click the Connect button.

Upon opening a connection, you are asked for your name. Enter your name and click Send. Your name is sent to the server as a JSON message over STOMP. After a one-second simulated delay, the server sends a message back with a “Hello” greeting that is displayed on the page. At this point, you can send another name or you can click the Disconnect button to close the connection.

### **Result of Test** :

![WebSocket](https://i.ibb.co/JnjYmv9/websocket.png)
