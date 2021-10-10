# Read: 11 - Spring

## What is Java Spring Boot?

- Java Spring Framework (Spring Framework) is a popular, open source, enterprise-level framework for creating standalone, production-grade applications that run on the Java Virtual Machine (JVM).

- Java Spring Boot (Spring Boot) is a tool that makes developing web application and microservices with Spring Framework faster and easier through three core capabilities:

- Autoconfiguration
- An opinionated approach to configuration
- The ability to create standalone applications

These features work together to provide you with a tool that allows you to set up a Spring-based application with minimal configuration and setup.

Steps to configure and run your first app:

From this link https://spring.io/guides/gs/serving-web-content/#scratch

Make the following :

Navigate to https://start.spring.io. This service pulls in all the dependencies you need for an application and does most of the setup for you.

Choose either Gradle or Maven and the language you want to use. This guide assumes that you chose Java.

Click Dependencies and select Spring Web, Thymeleaf, and Spring Boot DevTools.

Click Generate.

Download the resulting ZIP file, which is an archive of a web application that is configured with your choices.

or download it from here:
https://github.com/spring-guides/gs-serving-web-content/archive/main.zip

or you can clone this link:
git clone https://github.com/spring-guides/gs-serving-web-content.git

then cd into gs-serving-web-content/initial

Then create the web controller by make new class as will be as this path:
src/main/java/com/example/servingwebcontent/GreetingController.java

inside it put this code:

```
package com.example.servingwebcontent;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class GreetingController {

	@GetMapping("/greeting")
	public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
		model.addAttribute("name", name);
		return "greeting";
	}

}
```

Then create the html file (greeting.html) by make new class as will be as this path:
src/main/resources/templates/greeting.html
inside it put this code:

```
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Getting Started: Serving Web Content</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
    <p th:text="'Hello, ' + ${name} + '!'" />
</body>
</html>
```

To speed up refresh cycle (restarting your application, and refreshing the browser to view the change) add this to your gradle dependencies:

1. Enables hot swapping.

2. Switches template engines to disable caching.

3. Enables LiveReload to automatically refresh the browser.

4. Other reasonable defaults based on development instead of production.

spring-boot-devtools and enable hot swapping:

```
dependencies {
    developmentOnly("org.springframework.boot:spring-boot-devtools")
}
```

to run the application just go and run from this path:
src/main/java/com/example/servingwebcontent/ServingWebContentApplication.java

To test it go to:
http://localhost:8080/greeting
It must show you an html page with "Hello, World!" by default!

To know more, the resources from here:

https://spring.io/guides/gs/serving-web-content/
https://www.thymeleaf.org/doc/articles/springmvcaccessdata.html
