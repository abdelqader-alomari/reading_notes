## CSS Transforms:

it's new way to layout with alternative way to size, position, and change elements. it comes with two-dimensional and three-dimensional.

### Transform Syntax:

`div {
  -webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}`


### 2D Transforms:

Two-dimensional transforms work on the x and y axes, known as horizontal and vertical axes.

#### 2D Rotate

The rotate value provides the ability to rotate an element from 0 to 360 degrees. Using a positive value will rotate an element clockwise, and using a negative value will rotate the element counterclockwise. The default point of rotation is the center of the element, 50% 50%

`.box-1 {
  transform: rotate(20deg);
}`

#### 2D Scale

change the appeared size of an element. The default scale value is 1, any value between .99 and .01 makes an element appear smaller while any value greater than or equal to 1.01 makes an element appear larger.

`.box-2 {
  transform: scale(1.25);
}
`
The scaleX value will scale the width of an element while the scaleY value will scale the height of an element. To scale both the height and width of an element but at different sizes, the x and y axis values may be set simultaneously. To do so, use the scale transform declaring the x axis value first, followed by a comma, and then the y axis value.

`
.box-3 {
  transform: scale(.5, 1.15);
}
`

#### 2D Translate:

 works a bit like that of relative positioning. Using the translateX value will change the position of an element on the horizontal axis while using the translateY value will change the position of an element on the vertical axis.

 *Positive values will push an element down and to the right of its default position while negative values will pull an element up and to the left of its default position.*

`.box-3 {
  transform: translate(-10px, 25%);
}
`

#### 2D Skew:

Using the skewX value distorts an element on the horizontal axis while the skewY value distorts an element on the vertical axis. The distance calculation of the skew value is measured in units of degrees. Length measurements, such as pixels or percentages, do not apply here.

`.box-3 {
  transform: skew(5deg, -20deg);
}
`

#### Combining Transformers:

To combine transforms, list the transform values within the transform property one after the other without the use of commas.

**Using multiple transform declarations will not work, as each declaration will overwrite the one above it.**

`.box-1 {
  transform: rotate(25deg) scale(.75);
}`

#### Transform Origin:

The transform-origin property can accept one or two values. When only one value is specified, that value is used for both the horizontal and vertical axes. If two values are specified, the first is used for the horizontal axis and the second is used for the vertical axis.the values are treated like that of a background image position, using either a length or keyword value. That said, 0 0 is the same value as top left, and 100% 100% is the same value as bottom right.

`.box-4 {
  transform: scale(.75) translate(-10px, -10px);
  transform-origin: 20px 50px;
}
`

#### Perspective:

 three-dimensional transforms to work the elements need a perspective from which to transform.When you want to transform a group of elements all with the same perspective, or vanishing point, apply the perspective property to their parent element.

`.box {
  transform: perspective(200px) rotateX(45deg);
}`

#### Perspective Depth Value:

the length value will set the depth of the perspective. The higher the value, the further away the perspective appears
