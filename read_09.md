# Read: 09 - WRRC and Java

## The HTTP Request Lifecycle

![HTTP Request Lifecycle](https://csharpcorner-mindcrackerinc.netdna-ssl.com/article/introduction-to-iis-server-http-request-life-cycle-hosting-a-website-in-iis-se/Images/image005.png)

### Step 1: Local Processing

Depending on how in depth you want to get, much can happen during this step depending on the application making the request.

Your browser extracts the "scheme"/protocol (we have established that this will be HTTP), host (www.example.com),
and optional port number, resource path, and query strings that are specified in the form

` <protocol>://<host><:optional port>/<path/to/resource><?query>` . An example is ` |http|://|www.example.com||:5000||/mainpage||?query=param&query2=param2| `

Now that the browser has the intended hostname for the request, it needs to resolve an IP address1. The browser will then look through its own cache of recently requested URLs, the operating system’s cache of recent queries, your router’s cache, and your DNS cache.

### Step 2: Resolve an IP

If the cache lookup success the browser fires off DNS request using UDP3,The DNS request have your return IP in its header

the request will travel throws many network devices to reach its target DNS server,when its reach the network he will use the routing table to see which other devices is connected

when the request arrives to the server ,the server will look to your address associated that have the requested hostname ,if it find one then it will send response if not the DSN server cannot locate hostname then its pass he request to another DNS until he find one ,if he cannot find one he response with a failure and your browser returns an error.

if the request was successful then the requesting client has a target IP it will receive a part of information an tell you the how long will take to response

### Step 3: Establish a TCP Connection

Before the server can accept a three-way handshake, the client must first create a TCP connection. The server must be listening on a port and executing a passive open, after which the client can conduct an active open and the client-server connection will be recognized. This allows the receiver to restore the original order of received packets and the sender to restore the original order of sent packets.

### Step 4: Send an HTTP Request

The request is made up of a(request line), request header and a body.
The request line its line taht indicates the HTTP method.
The header of the request is made up of pairs in the form name:value CR and LF
both CR and LF indicate the end of the header section
Host which contain both domain and port taht the request is sended to .
common standard HTTP header fields include Origin, Accept, Accept-Encoding.
the body content of an HTTP request is completely optional but we prefer to send the data in json format.
when the HTTP request is sent and in correct way the server will process the request and send back an response .

### Step 5: Tearing Down and Cleaning Up

After receiving the response, the client sends a TCP FIN packet, to which the server answers with an ACK, and then sends its own FIN, to which the client responds with its own ACK signal. Then there will be a timeout. The four-way handshake is what it’s called. The browser begins to process the information it has received and then exits.

## Do a Simple HTTP Request in Java

![HTTP Java](https://th.bing.com/th/id/R.8e9b37501a4fdeb5bcb6d34fd79e7729?rik=k64v4UI8wr8ZCw&riu=http%3a%2f%2f2.bp.blogspot.com%2f-Hwojng51zj0%2fTWNVDX_I9TI%2fAAAAAAAAAAg%2foW3EQKhFHHQ%2fs400%2fJava__GET%2bmethod%2bof%2bHTTP%2bRequest.jpg&ehk=lDy8EW%2fvSvJtsJ3LP%2f9bdPAzvMrOPXgHzfbk5zWcMas%3d&risl=&pid=ImgRaw&r=0)

The HttpUrlConnection class allows basic HTTP queries to be made without the use of any extra libraries, and the classes we require are included in the java.net package. Set the requestMethod property to one of the following values for all sorts of requests: GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE.

- Add Request Parameters
- Setting Request Headers
- Configuring Timeouts
- Handling Cookies
- Handling Redirects
- Reading the Response
- Reading the Response on Failed Requests
- Building the Full Response

Use HttpUrlConnection class –> openConnection() method , ex:

```
URL url = new URL("http://example.com");
HttpURLConnection con = (HttpURLConnection) url.openConnection();
con.setRequestMethod("GET");
```

–> doOutput property to true, then write a String of the form param1=value¶m2=value to the OutputStream of the HttpUrlConnection instance, ex:

```
Map<String, String> parameters = new HashMap<>();
parameters.put("param1", "val");
```

con.setDoOutput(true);
DataOutputStream out = new DataOutputStream(con.getOutputStream());
out.writeBytes(ParameterStringBuilder.getParamsString(parameters));
out.flush();
out.close();
ParameterStringBuilder containing a static method, getParamsString(), that transforms a Map into a String

–> setRequestProperty() method –> getHeaderField() method –> setting the connect and read timeouts setConnectTimeout() and setReadTimeout() methods –> handle cookies by CookieManager and HttpCookie and many more (Read the cookie -> add it to cookie store -> add the cookies to the request)
–> enable or disable automatically following redirects for a specific connection setInstanceFollowRedirects() method –> read the response getResponseCode(), connect(), getInputStream() or getOutputStream() methods –> read response on failed requests HttpUrlConnection.getErrorStream() –> Building the Full Response.

---

## Resources:

https://dev.to/dangolant/things-i-brushed-up-on-this-week-the-http-request-lifecycle-

https://www.baeldung.com/java-http-request

https://google.com
