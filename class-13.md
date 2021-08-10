### Read : Class 13 - Status Codes Based On REST Methods

**100’s = information messages (informative)**
**200’s = 200-299 indicates that request is successful**
**300’s = redirection group**
**400’s = request problem, indicates error in client side.**
**500’s = errors from server side.**

---

### **What is a status code 202?**

Accepted

### **What is a status code 308?**

Permanent redirect

### **What code would you use if an update didn’t return data to a client?**

204 No Content - A proper code for updates that don’t return data to the client, for example when just saving a currently edited document.

### **What code would you use if a resource used to exist but no longer does?**

410 Gone - This is like 404 but we know that the resource existed in the past, but it got deleted or somehow moved, and we don’t know where.

### **What is the ‘Forbidden’ status code?**

403 Forbidden - The client has authorized or doesn’t need to authorize itself, but still has no permissions to access the resource.

---
