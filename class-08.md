## Read: Class 08 - API Design Best Practices

### **What does REST stand for?**

The term REST stands for Representational State Transfer. It is an architectural style that defines a set of rules in order to create Web Services.

### **REST APIs are designed around a.**

designed around resources, which are any kind of object, data, or service that can be accessed by the client.

### **What is an identifer of a resource? Give an example.**

a URI that uniquely identifies that resource, for example user input for city name to get location and weather data.

### **What are the most common HTTP verbs?**

GET, POST, PUT, PATCH, and DELETE.

### **What should the URIs be based on?**

URIs should be based on nouns (the resource)

### **Give an example of a good URI.**

example of a good URL is http://www.microsoft.com, which is the link to Microsoft's web page. A URL, which stands for uniform resource locator, is a formatted text string used by web browsers and other software to identify a network resource on the Internet.

### **What does it mean to have a ‘chatty’ web API? Is this a good or a bad thing?**

"chatty" web APIs that expose a large number of small resources. Such an API may require a client application to send multiple requests to find all of the data that requires.
bad or good? It's a bad thing and we should avoid using it.

### **What status code does a successful GET request return?**

HTTP status code 200 (OK).

### **What status code does an unsuccessful GET request return?**

HTTP status code 404 (Not Found).
or If not valid, 400 Bad Request is returned

### **What status code does a successful POST request return?**

HTTP status code 201 (Created).

### **What status code does a successful DELETE request return?**

What status code does a successful DELETE request return? Ans: Responses. If a DELETE method is successfully applied, there are several response status codes possible: A 202 ( Accepted ) status code if the action will likely succeed but has not yet been enacted. A 204 ( No Content ) status code if the action has been enacted and no further information is to be supplied.

## Things I want to know more about

More about API, HTTP Verbs(GET, POST, PUT, PATCH, and DELETE.) errors types and dealing with it.

---
