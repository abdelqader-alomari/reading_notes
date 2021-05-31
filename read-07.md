### Read: 07 - HTML Tables; JS Constructor Functions:

## Domain Modeling
Domain modeling is the process of creating a conceptual model for a specific problem. And a domain model that's articulated well can verify and validate your understanding of that problem.

### Define a constructor and initialize properties:

| Property     | Data              | Type    |
|--------------|-------------------|---------|
| `epicRating` | `1` to `10`       | Number  |
| `hasAnimals` | `true` or `false` | Boolean |

* The new keyword instantiates (i.e. creates) an object.
* The constructor function initializes properties inside that object using the this variable.
* The object is stored in a variable for later use.


 * methods can be added to a constructor function's **prototype**. Think of the prototype as an object's stunt double. Whenever a scene is too dangerous, you can substitute in the prototype to do the work while the object takes all the glory.

 ### Calculate Weekly Likes:

Popularity of a video is measured in Likes. And the formula for calculating Likes is the number of viewers times the percentage of viewers who'll Like a video. In other words, **viewers times percentage**.

To calculate the number of viewers per day, generate a random number between 10 and 30 and then multiply it by the epic rating of that video.

| Random number | Epic rating | Viewers per day |
|---------------|-------------|-----------------|
| 10            | 10          | 100             |
| 20            | 9           | 180             |
| 30            | 8           | 240             |

The percentage of viewers who'll Like a video depends on whether or not the video contains animals.

| Animals | Percentage |
|---------|------------|
| Yes     | 75%        |
| No      | 40%        |

```javascript
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

EpicFailVideo.prototype.dailyLikes = function() {
  var viewers, percentage;

  viewers = this.generateRandom(10, 30) * this.epicRating;

  if (this.hasAnimals) {
    percentage = 0.75;
  } else {
    percentage = 0.40;
  }

  return Math.round(viewers * percentage);
}

EpicFailVideo.prototype.weeklyLikes = function() {
  var total = 0;

  for (var i = 0; i < 7; i++) {
    total += this.dailyLikes();
  }

  return total;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.weeklyLikes());
console.log(corgiFail.weeklyLikes());
```

The `weeklyLikes()` method on `EpicFailVideo`'s prototype is assigned a function with no parameters. This method starts by declaring a `total` variable that's initialized to `0`.

The `weeklyLikes()` method proceeds to call `this.dailyLikes()` seven times and adds the returning number of Likes to `total` using the `+=` operator. Afterwards, `total` is returned.

When `weeklyLikes()` is called on both `parkourFail` and `corgiFail`, the returning value is logged to the console.

- - -

## Tables:

### What's a Table?
A table represents information in a grid format. Grids allow us to understand complex data
by referencing information on two axes. Each block in the grid is referred to as a table cell.
In HTML a table is written out row by row.

* The `<table>` element is used to create a table. which is written out row by row.
* Table row `<tr>` indicate the start of each row.
* Table data `<td>` represents each cell of a table.
* The <th> element is used just
* Table heading `<th>` represents the heading for a column or a row.
* The colspan attribute can be used on a `<th>` or `<td>` element
  and indicates how many columns that cell should run across.
* The rowspan attribute can be used on a `<th>` or `<td>` element
  to indicate how many rows a cell should span down the table.
* `<thead>` contain The headings of the table.
* `<tbody>` The table body should sit inside this element.
* `<tfoot>` The footer belongs inside the this element.

- - -

## Functions, Methods, and Objects:

### Creating an Object: Constructor Notation:
The new keyword and the object constructor create a blank object.
You can then add properties and methods to the object.

```javascript
// update the value of properties.
Car.name = 'Toyota';
// here the car is the object, name is the property name, 'Toyota' is property value, '.' dot notation
```
#### Create the Object, then add properties and methods

![Create the Object](https://i.ibb.co/RPbjyYp/Create-the-Object.png)

#### Create the Object with properties and methods:

![Object with properties and methods](https://i.ibb.co/J5kN0FD/Object-with-properties-and-methods.png)


### What are built-in Objects?

![Built-in Objects](https://i.ibb.co/zNnv4xg/Built-in-Objects.png)

#### Browser Object Model (BOM):
The browser object model creates a model of the browser tab or window.
~[Browser Object Model](https://sharryhong.github.io/image/bom.jpg)

#### examples:
* `window.print();` this method cause the browser's print dialog box to be shown.
* `window.screen.width;` find the width of device's screen in pixels.

#### Global JavaScript Objects:
A group of individual objects that relate to different parts of JS language.
* The names of the global objects starts with a Capital letter.
* Dates: to represents and handle the date.
* Math: for working with numbers and calculations
* Regex: for matching patterns within strings of text

#### examples of using methods:
1. DOM:
    * `getElementById()` gets an element by the value of its Id.
    * `document.lastModified;` that property tell you the date that the page last updated
2. Global JavaScript Objects:
    * `object.toUpperCase();` makes all leters uppercase.
    * `Math.PI();` return the value of pi


### Window Properties:
The window object has a slew of properties that can tell you (the programmer) about its properties. Skim through these properties and try clicking on their names to see output in the JavaScript console.

| Property | Description |
|--------- |------------ |
| title | Title of current document |
| lastModifed | Date on which document last modified |
| URL | Returns string containing URL of current documet |
| domain | Return domain of current document |
| closed | Returns True if window is closed |
| defaultStatus | Set the text on the status bar |
| innerHeight | The inner height of the page (not including toolbar, other tabs, etc) |
| innerWidth | The inner width (excludes toolbar, other tabs, etc.) |
| outerHeight | The outer height of a window (including toolbar, other tabs, etc) |
| outerWidth | The outer width of a window |
| location | Window's current URL |
| name | Name of the window |
| parent | Used with frames to refer to the window that created a particular window or is one level up from the frame |
| parent | Reference to the window that the current window came from |
| pageXOffset | The number of pixels user has scrolled horizontally from the upper-left corner of document |
| pageYOffset | The number of pixels the user has been scrolled vertically |
| screenX | Horizontal coordinate of the window relative to the screen |
| screenY | Vertical coordinate of the window relative to the screen |
| top | The top-most parent window |

### Window Methods:
| Method | Description |
|------- |------------ |
| `alert()` | Opens a popup window. User must click OK to close |
| `prompt()` | Prompts user for an input |
| `open()` | Opens new browser window with specified URL |
| `close()` | Closes window |
| `print()` | Opens print dialog |

### String Objects:

![String Objects](https://i.ibb.co/MpBk0hv/String-Objects.png)

### Date Object and Time:

![Data Objects](https://www.htmlgoodies.com/wp-content/uploads/2021/04/js2_ch2_img_21.jpg)