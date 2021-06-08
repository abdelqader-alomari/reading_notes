## CSS Transforms:

![CSS Transforms](https://miro.medium.com/max/900/1*_6MfwckxNfQTca9SiG8MdQ.png)

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

![Transforms](https://www.dmxzone.com/downloads/images/css_transforms_ss.png)

## CSS Transitions:

* for a transition to take place, an element must have a change in state, and different styles must be identified for each state. The easiest way for determining styles for different states is by using the :hover, :focus, :active, and :target pseudo-classes.

* There are four transition related properties in total, including transition-property, transition-duration, transition-timing-function, and transition-delay. Not all of these are required to build a transition, with the first three are the most popular.

`.box {
  background: #2db34a;
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
}`

### Transitional Property

transition-property property determines exactly what properties will be altered in conjunction with the other transitional properties and  identified within the transition-property value will be affected by any transitions.

#### Transitional Properties

* background-color 
* background-position
* border-color 
* border-width 
* border-spacing 
* bottom 
* clip 
* color 
* crop
* font-size
* font-weight
* height
* left
* letter-spacing
* line-height
* margin
* max-height
* max-width
* min-height
* min-width
* opacity
* outline-color
* outline-offset
* outline-width
* padding
* right
* text-indent
* text-shadow
* top
* vertical-align
* visibility
* width
* word-spacing
* z-index

### Translation Timing:

The duration in which a transition takes place is set using the transition-duration property. The value of this property can be set using general timing values, including seconds (s) and milliseconds (ms). These timing values may also come in fractional measurements, .2s for example. you can set it for multiple by separate values by comma.


### Transition Delay

On top of declaring the transition property, duration, and timing function, you can also set a delay with the transition-delay property. The delay sets a time value, seconds or milliseconds, that determines how long a transition should be stalled before executing. As with all other transition properties, to delay numerous transitions, each delay can be declared as comma separated values.

#### Shorthand:

`transition: background .2s linear, border-radius 1s ease-in 1s;`


## Animations:

![Summary of Animations in picture](https://webartdevelopers.com/blog/wp-content/uploads/2018/10/Motion-UI-CSS-Animation-Library.gif)

CSS animations allow you to build complex animated sequences. Like transitions, they manipulate the CSS properties that control how interface elements appear. Unlike transitions, they are not tied to shifts between style sheets that distinguish interface states.

### Animations Keyframes:

to create animation use  @keyframes rule includes the animation name, any animation breakpoints, and the properties intended to be animated.

[Simulator site to show CSS Animations](https://designlink.work/responsive-simulator/animatecss/)
