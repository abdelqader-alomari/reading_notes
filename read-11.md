### Read: 11 - Assorted Topics:

## CSS Images:

### Controlling sizes of images in CSS:

width: value; height: value, are used to control size of images.
HTML and CSS code will often load before the images, and telling the browser
how much space to leave for an image allows it to render the rest of the page
without waiting for the image to download.

example of image sizes that are commonly used on all pages:
* Small portrait: 220 x 360
* Small landscape: 330 x 210
* Feature photo: 620 x 400

### Align images:

* float property used to align images right or left
* to center the image, use display: block; to turn it to a block element,
  then use margin: 0px auto; to give margin top and bottom 0 px, and auto margin left and right which make the picture at the middle.

### Background Images:

* background-image: url(" "); to pick an image from url and make it as background.
* background-repeat: repeat; repeat the background image horizontally and vertically.
* background-repeat: repeat-x; the image repeated horizontally.
* background-repeat: repeat-y; the image repeated vertically.
* no repeat: the image is only show once.
* fixed: the background image stayed on the same position in the page.
* scroll: the background images moves up and down as user scrolls up and down.

### Background Position:

* background-position: left top;
* background-position: left center;
* background-position: left bottom;
* background-position: center top;
* background-position: center center;
* background-position: center bottom;
* background-position: right top;
* background-position: right center;
* background-position: right bottom;

*we can use percentage also, background-position: 50% 50%;*

**Shorthand: example: we can use {background: #ffffff url("images/tulip.gif")
no-repeat top right;}

the order like this:
1. background-color
2. background-image
3. background-repeat
4. background-attachment
5. background-position

### Image Rollovers & Sprites:

when a link or button changes to a second style when a user moves their mouse over it.
This is achieved by setting a background image for the link or button that has three different styles of the same button.

**Spirte: single image is used for several different parts of an interface.**

#### Constrast of Background Images:

* High contrast
* Low contrast
* screen
*If we want to overlay text on background image, we must use low contrast.*

- - -

## Practical Information:

![SEO](https://th.bing.com/th/id/Rd0fd0e8440308bf2fefa7e69e971586f?rik=wvTd23taPLdb7A&riu=http%3a%2f%2fwww.search-usability.com%2fimages%2fseo-program.png&ehk=2KbvCTD1cpAKqkemTMQZeDvQY88MxqpqPxT1zh9qFeU%3d&risl=&pid=ImgRaw)

**SEO: Search Engine Optimization; the name reflects the functionality of it.**

### On page SEO:

**seven key places where keywords in every page of website:**

1. Page title
2. URL / Web address
3. Headings
4. Text
5. Link Text
6. Image Alt Text
7. Page Description


### Identify Keywords and phrases:

1. BrainStorm
2. Organize
3. Research
4. Compare
5. Refine
6. Map

### Summary from the book:

* Search engine optimization helps visitors find your sites when using search engines.
* Analytics tools such as Google Analytics allow you to see how many people visit
  your site, how they find it, and what they do when they get there.
* To put your site on the web, you will need to obtain a domain name and web hosting.
* programs allow you to transfer files from your local computer to your web server.
* Many companies provide platforms for blogging, email newsletters, e-commerce and
  other popular website tools (to save you writing them from scratch).
