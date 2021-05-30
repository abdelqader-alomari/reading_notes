### Read: 06 - JS Object Literals; The DOM:

## Objects:
Objects group together a set of variables and functions to create a model of a something you would recognize from the real world.

* Objects consists of property and method, If a variable is part of an object, it is called a property. Properties tell us about the object
* If a function is part of an object, it is called a method. Methods represent tasks that are associated with the object.

### Example:

* In real life, a car is an object.

* A car has properties like weight and color, and methods like start and stop:

![Object](https://i.ibb.co/vwBhVb1/Object.png)

* All cars have the same properties, but the property values differ from car to car.

* All cars have the same methods, but the methods are performed at different times.

* properties and methods have a name and a value. In an object, that name is called a key. An object cannot have two keys with the same name.
The value of a method is always a function.

### Creating an Object: Literal notation: 
![Literal notation](https://i.ibb.co/FX8BBD4/Literal-Object.png)

* Dot notation: to access a property or method of an object you use the name of the object followed by (.) -which is called period or member operator then the name of property or method you want to access.

* Objects makes work easy with less effort and without repeat, alot of things have same propertes and methods but in just different of values!

- - -

## Document Object Model (DOM):

The Document Object Model (DOM) specifies how browsers should create a model of an HTML page and how JavaScript can access and update the
contents of a web page while it is in the browser window.

![DOM benefits](https://i.ibb.co/16h0ZFy/What-can-do-Java-Script-do-with-DOM.png)

* In HTML The DOM specifies the way in which the browser should structure this model using a DOM tree which is made by objects Each object Represents a different part of the page loaded in the browser window.

* Application Programming Interface (API).User interfaces let humans interact with programs; APls let programs (and scripts) talk to each other. 
* The DOM states what your script can "ask the browser about the current page, and how to tell the browser to update what is being shown to the user.

![DOM model](https://1.bp.blogspot.com/-c1VhRCxc4ds/X5938GT76GI/AAAAAAAACFU/yzX7a1aIinIR_i4sy7dSIW9z8Q5mgX72QCLcBGAsYHQ/s732/dom1.png)

* As a browser loads a web page, it creates a model of that page.
The model is called a DOM tree, and it is stored in the browsers' memory.
* It consists of four main types of nodes:
Document Node, Element Node, Attribute Node, and Text Node.

* Accessing and updating the DOM tree involves two steps:
1: Locate the node that represents the element you want to work with.
2: Use its text content, child elements, and attributes.

* Finding Elements: we can find elements by: 
1) ID 		2) Tag name 		3) Class name

* Methods that find elements in the DOM tree are called DOM queries.
to store the result of the query using the variable by this way in picture:
![Store Query](https://i.ibb.co/HY6R2q2/store.png)

### Methods to return elements:

#### Return single element:

![Return single element](https://i.ibb.co/Lxw1yVL/methods-to-return-single-element-node.png)

#### Return multiple elements:

![Return multiple elements](https://i.ibb.co/MBSVqXf/methods-to-return-multiple-elements-node.png)

#### getElementbyID:
![getelementbyid](https://i.ibb.co/wR9bgKS/getelementbyid.png)

### Nodelist:
* When a DOM method can return more than one element, it returns a Nodelist
* A Nodelist is a collection of element nodes. Each node is given an index number (a number that starts at zero, just like an array). it's called collection.

#### Live and static Nodelists:
* In a live Nodelist, when your script updates the
page, the Nodelist is updated at the same time. returns by getEl ementsBy...
* In a static Nodelist when your script updates the page, the NodeList is not updated to reflect the changes made by the script. return by querySelector...


### Looping through a nodelist: 
![Looping](https://pbs.twimg.com/media/D9MtwvfWkAICWOX.jpg)


### Traversing the DOM:

You can do it by using 5 properties:
parentNode, previousSibling/nextSibling, firstChild/lastChild

![DOM Tree](https://www.qualitestgroup.com/images/howto/DOMTree_HowTo.png)


### Adding elements using DOM manipulation:

1. Create the element: createElement( )
2. Give it content: createTextNode ( ) * you can skip if you add empty element
3. add it to the DOM: appendChild ( )


### Attribute Nodes:

* getAttribute( ) get the value of an atribute
* hasAttribute( ) checks if element node has a specified attribute
* setAttribute( ) sets the value of an attribute
* removeAttribute( ) removes an attribute from an element mode

- - -

## Understanding the problem domain is the hardest part of programming:

### If understanding the problem domain is the hardest part of programming and you want to make programming easier, you can do one of two things:

* Make the problem domain easier
* Get better at understanding the problem domain
* You can often make the problem domain easier by cutting out cases and narrowing your focus to a particular part of the problem.

* What does it mean is that it is often beneficial to take a part of the problem and fully understand that part before expanding the problem domain.

* Games are really good at this.  Look at most games today and you’ll find that you start with a very small problem domain.  The first level is usually a tutorial that has a basic set of things you can do so that you don’t get overwhelmed.  But, as you advance through the levels, you usually find they get harder and introduce new concepts that build gradually on what you know, until you understand a pretty large problem domain.