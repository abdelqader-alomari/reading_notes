### Read: 13 - Local Storage

![HTML5 Local Storage](https://javabeat.net/wp-content/uploads/2013/10/html5-localStorage.png)

## Local Storage for Web Applications

Local storage is part of the HTML5 Web Storage API and it allows you to store data in the browser. Unlike cookies, data stored using local storage isn’t sent back to the server. All data stays on the client, and you can currently store from 2MB to 10MB. This limit is tied to the specific browser, protocol (HTTP or HTTPS), port, and top level domain in use.

**Potentially Dealbreaking Downsides:**

* Cookies are included with every HTTP request, thereby slowing down your web application by needlessly transmitting the same data over and over
* Cookies are included with every HTTP request, thereby sending data unencrypted over the internet (unless your entire web application is served over SSL)
* Cookies are limited to about 4 KB of data — enough to slow down your application (see above), but not enough to be terribly useful

### LOCAL STORAGE HACKS BEFORE HTML5:

- userData allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure.
- intranet sites:Trusted domains can store 10 times that amount.And hey, 640 KB ought to be enough for anybody.

 Local Shared Objects allows Flash objects to store up to 100 KB of data per domain.

 ### HTML5 STORAGE

 HTML5 Storage: it’s a way for web pages to store named key/value pairs locally, within the client web browser.


 ### STORAGEEVENT OBJECT

| PROPERTY | DESCRIPTION |
| -------- | ----------- |
| key | named key that was added, removed, or modified |
| oldValue | the previous value (now overwritten), or null if a new item was added |
| newValue | the new value, or null if an item was removed |
| url* | the page which called a method that triggered this change |


## Use HTML local storage:

### Remove Single Row:

`<script type="text/javascript>
localStorage.removeItem(key); //Remove A Single Desired KEY From Local Storage
</script>`

### Insert A Single Row:

`<script type="text/javascript>
localStorage.setItem("key", "value"); //Set A Single Desired KEY-VALUE In Local Storage
</script>`

### Get A Single Row:

`<script type="text/javascript>
var getValue = localStorage.getItem("key"); //Get A Single Desired KEY's VALUE From Local Storage
</script>`

### Remove All Rows:

`<script type="text/javascript>
localStorage.clear(); //Clear All Local Storage KEY-VALUE
</script>`

![Local Storage](https://th.bing.com/th/id/R77e900fe84ec06e298f0404f8e5cf1e4?rik=p6D0Vnf3dlA8sg&riu=http%3a%2f%2fwww.exeideas.com%2fwp-content%2fuploads%2f2016%2f02%2fUse-HTML5-Local-Storage.jpg&ehk=vo7URAnfnYvMeP1cE2kHqO9qvePe%2bNN5BGtVB5PaCKI%3d&risl=&pid=ImgRaw)

