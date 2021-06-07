### Read: 12 - Docs for the HTML <canvas> Element & Chart.js

![Power of chart.js](https://raw.githubusercontent.com/coroo/chart-js-integration/gh-pages/assets/img/chart-js-integration.gif)

A great way to get started with charts is with Chart.js, a JavaScript plugin that uses HTML5’s canvas element to draw the graph onto the page. that makes using all kinds of bar charts, line charts, pie charts and more, incredibly easy.

## Setting up:

The first thing we need to do is download directly from here: (Chart.js)[https://registry.npmjs.org/chart.js/-/chart.js-3.3.2.tgz] Copy the Chart.min.js out of the unzipped folder and into the directory you’ll be working in. Then create a new html page and import the script Chart.min.js

to prepare for Charts we need to add canvas element to the body of HTML:

example: `<canvas id="buyers" width="600" height="400"></canvas>`

and we need also to  write a script that will retrieve the context of the canvas, so add as example this to the foot of your body element:

`<script>
    var buyers = document.getElementById('buyers').getContext('2d');
    new Chart(buyers).Line(buyerData);
</script>`



## Drawing a line chart:
Inside the same script tags we need to create our data, in this instance it’s an object that contains labels for the base of our chart and datasets to describe the values on the chart. Add this immediately above the line that begins ‘var buyers=’:

`var buyerData = {
	labels : ["January","February","March","April","May","June"],
	datasets : [
		{
			fillColor : "rgba(172,194,132,0.4)",
			strokeColor : "#ACC26D",
			pointColor : "#fff",
			pointStrokeColor : "#9DB86D",
			data : [203,156,99,251,305,247]
		}
	]
}`

## Drawing a bar Chart:

same process of creating line chart but instead of use .line like here:
`new Chart(buyers).Line(buyerData);` we use .Bar with name of variables for Bar Chart. and fill the data to draw.

## Drawing Pie Chart:

This will be easier, first use .Pie in new Chart instead of .Line as in Line Chart...
and the data will be simple just contain value and color.

![Sample of Charts](https://i.ibb.co/x3QzL4L/Charts.png)

- - - 

## Canvas API

### Basic usage of canvas:

#### The `<canvas>` element:

`<canvas>` element has only two attributes, width and height. These are both optional.

if you didn't set them, canvas will initially be 300 pixels wide and 150 pixels high

 The element can be sized by CSS but must respect atio of the initial canvas.

 The `<canvas>` element creates a fixed-size drawing surface that exposes one or more rendering contexts
 `getContext()` used to obtain the rendering context and its drawing functions. it takes one parameter, the type of context. For 2D graphics

 **to check support you can using if...else statement**

### Drawing shapes with canvas

#### The grid

![grid](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API/Tutorial/Drawing_shapes/canvas_default_grid.png)

The origin of this grid is positioned in the top left corner at coordinate (0,0). All elements are placed relative to this origin. So the position of the top left corner of the blue square becomes x pixels from the left and y pixels from the top, at coordinate (x,y).

#### Drawing Rectangles

* fillRect(x, y, width, height): Draws a filled rectangle
* strokeRect(x, y, width, height): Draws a rectangular outline
* clearRect(x, y, width, height): Clears specified rectangular area(fully transparent)

#### Drawing Paths:

1. create the path.
2. use drawing commands to draw into the path.
3. stroke or fill the path to render it.

* beginPath(): Creates a new path
* moveTo(): the first path of starting posiotion We also use to draw unconnected paths
* Path methods: Methods to set different paths for objects.
* closePath(): Adds a straight line to the path, go to the start of current sub-path.
* stroke(): Draws the shape by stroking its outline.
* fill(): Draws a solid shape by filling the path's content area.

#### Drawing different Shapes:

* Draw Lines: lineTo(x, y)
* Draw Arcs: arc(x, y, radius, startAngle, endAngle, counterclockwise) or 
  arcTo(x1, y1, x2, y2, radius)
* Bezier curves: bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)
* Quadratic curves: quadraticCurveTo(cp1x, cp1y, x, y)
* Rectangles: rect(x, y, width, height)
* Path2D()objects: contain all path methods like moveTo, rect, arc or quadraticCurveTo

**Path2D API is using SVG path data to initialize paths on your canvas, allow you to  pass around path data and re-use them in both, SVG and canvas.**

- - -

## Applying styles and colors

### Colors:

* fillStyle = color: Sets the style used when filling shapes.
* strokeStyle = color Sets the style for shapes' outlines.

#### Transparency:

globalAlpha = transparencyValue: the value between 0.0 to 1.0

### Line Styles:

* lineWidth = value: Sets the width of lines drawn
* lineCap = type Sets the appearance of the ends of lines (butt, round, square)
* lineJoin = type of the appearance of "corners" where lines meet.(round,bevel,miter)
* miterLimit = value Establishes a limit on the miter when two lines join at a sharp
  angle, to let you control how thick the junction becomes.
* getLineDash() Returns the current line dash pattern array containing an even number 
  of non-negative numbers.
* setLineDash(segments): Sets the current line dash pattern.
* lineDashOffset = value Specifies where to start a dash array on a line.

#### Gradients:

1. Linear Gradient: createLinearGradient(x1, y1, x2, y2)
2. Radial Gradient: createRadialGradient(x1, y1, r1, x2, y2, r2)
3. Conic Gradient: createConicGradient(angle, x, y)

* addColorStop(): assign colors to gradient
* gradient.addColorStop(position, color): Creates a new color stop between 0.0 - 1.0

#### Paterns:

createPattern(image, type): Creates and returns a new canvas pattern object. image

types of patterns:
* repeat: Tiles the image in both vertical and horizontal directions.
repeat-x: Tiles the image horizontally but not vertically.
repeat-y: Tiles the image vertically but not horizontally.
no-repeat: Doesn't tile the image. It's used only once.

#### Shadows:

* shadowOffsetX = float Indicates the horizontal distance the shadow should extend from the object. This value isn't affected by the transformation matrix.default is 0
* shadowOffsetY = float Indicates the vertical distance the shadow should extend from the object. This value isn't affected by the transformation matrix. The default is 0.
* shadowBlur = float Indicates the size of the blurring effect; .Default value is 0.
* shadowColor = color A standard CSS color value indicating the color of the shadow
  effect; by default, it is fully-transparent black.

## Drawing Text:

* fillText(text, x, y [, maxWidth]) Fills a given text at the given (x,y) position.
* strokeText(text, x, y [, maxWidth]) Strokes a given text at given (x,y) position. 

### Styling Text: 

font = value: The current text style being used when drawing text. This string uses the same syntax as the CSS font property. The default font is 10px sans-serif.
textAlign = value: Text alignment setting. Possible values: start, end, left, right or center. The default value is start.
textBaseline = value: Baseline alignment setting. Possible values: top, hanging, middle, alphabetic, ideographic, bottom. The default value is alphabetic.
direction = value: Directionality. Possible values: ltr, rtl, inherit. The default value is inherit.

![Canvas](https://th.bing.com/th/id/R89f8e9be4234fb000ef052c9c1f7b8ee?rik=IV4uzLFkLjRvog&riu=http%3a%2f%2fwww.programmingbasics.org%2fen%2fdownloads%2fhtml5canvas%2fimg%2fhtmlcanvas+-+128.png&ehk=vkFN78Ov%2fury7c0F%2bhCiu9qsjMPRvkAioMbXjmNqZw0%3d&risl=&pid=ImgRaw)

