# HTML and CSS concepts

---

## CSS
<p>
Cascading Style Sheets (CSS) is a stylesheet language used to describe the presentation of a document written in HTML or XML (including XML dialects such as SVG, MathML or XHTML). CSS describes how elements should be rendered on screen, on paper, in speech, or on other media. below are the important topics that everyone learn before diving to style any page.
</p>

* Box Model
* Positioning
* Common CSS structural classes
* Common CSS syling classes
* CSS Specificity
* CSS Responsive Queries
* Flexbox/Grid

---

## Box Model
<p>
According to the box model concept, every element on a page is a rectangular box and may have width, height, padding, borders, and margins.There are several properties that determine the size of that box.
</p>

* Width
* Height
* Padding
* Margin
* Borders

![Box Model](https://learn.shayhowe.com/assets/images/courses/html-css/opening-the-box-model/box-model.png)

### Width:
<p>
The default widthof an elements dependson its display value. Block-level elements have a default widthof 100%,
covers the entire horizontal space available.Inline and inline-block elements expand and contract horizontally to accommodate their content. Inline-level elements cannot have a fixed size, thus the width and height properties are only relevant to non-inline elements.To set a specific width for a non-inline element, use the width property:
</p>

<br>

```css
div {
  width: 400px;
}
```

<br>

### Height:
<p>
The default height of an element is determined by its content. Any element will expand and contract vertically as necessarily to accommodate its content. To set a specific height for a non-inline element, use the height property:  
</p>

<br>

```css
div {
  height: 100px;
}
```
<br>

### Margin:
<p>
The margin property allows us to set the amount of space that surrounds an element.Margins for an element fall outside of any border and are completely transparent in color. Margin can be used to specify the proper safe distance between the elements. You can set margins to four different direction i.e top, bottom, left and right.
Top and Bottom, are not accepted by inline-level elements. These vertical margins are, however, accepted by block-level and inline-block elements.
</p>

<br>

```css
div {
    margin : 20px /* sets margin of 20px to all direction. */
    margin : 20px 10px /* sets margin of 20px to top and bottom, margin of 10px to left and right direction. */
    margin : 5px 10px 15px 20px /* sets margin of 5px to top, margin of 10px to right, margin of 15px to bottom and margin of 20px to left. 
    */
}
```
<br>

### Padding:
<p>
The padding property is very similar to the margin property; however, it falls inside of an element’s border, should an element have a border. The padding property is used to provide spacing directly within an element.The padding property, unlike the margin property, works vertically on inline-level elements.
</p>

<br>

```css
div {
    padding : 20px /* sets padding of 20px to all direction. */
    padding : 20px 10px /* sets padding of 20px to top and bottom, padding of 10px to left and right direction. */
    padding : 5px 10px 15px 20px /* sets padding of 5px to top, padding of 10px to right, padding of 15px to bottom and padding of 20px to left. 
    */
}
```
<br>

### Borders:

<p>
Borders fall between the padding and margin, providing an outline around an element. The border property requires three values: width, style, and color. Shorthand values for the border property are stated in that order—width, style, color. In longhand, these three values can be broken up into the border-width, border-style, and border-color properties. These longhand properties are useful for changing, or overwriting, a single border value.
</p>

<p>
Here is the code for a 6-pixel-wide, solid, gray border that wraps around all four sides of a div.
</p>

<br>

```css
div {
  border: 6px solid #949599;
}
```

<br>

---

## Positioning:
<p>
The position property specifies the type of positioning method used for an element.
</p>
<p>
There are five different position values:
</p>

* static
* relative
* absolute
* fixed 
* sticky

### Static:
<p>
HTML elements are positioned static by default.Static positioned elements are not affected by the top, bottom, left, and right properties. An element with position static is not positioned in any special way; it is always positioned according to the normal flow of the page:
</p>

<br>

```css
 div{
     position: static;
 }
```
<br>

### Relative:
<p>
An element with position relative is positioned relative to its normal position.Setting the top, right, bottom, and left properties of a relatively-positioned element will cause it to be adjusted away from its normal position. Other content will not be adjusted to fit into any gap left by the element.
</p>

<br>

```css
 div{
     position: relative;
     left: 30px;
 }
```
<br>

### Absolute:
<p>
An element with position: absolute; is positioned relative to the nearest positioned ancestor (instead of positioned relative to the viewport, like fixed).However, if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling.
</p>

<br>

```css
 div{
     position: absolute;
     left: 30px;
 }
```
<br>

### Fixed:
<p>
An element with position fixed is positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element.A fixed element does not leave a gap in the page where it would normally have been located.
</p>

<br>

```css
 div{
     position: fixed;
     left: 30px;
 }
```
<br>

### Static:
<p>
An element with position sticky  is positioned based on the user's scroll position.A sticky element toggles between relative and fixed, depending on the scroll position. It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed.
</p>

<br>

```css
 div{
    position: -webkit-sticky; /* Safari */
    position: sticky;
    left: 30px;
 }
```

<br>

---

## Common CSS Structural Classes:

<p>
    Structural pseudo classes allow access to the child elements present within the hierarchy of parent elements. We can select first-child element, last-child element, alternate elements present within the hierarchy of parent elements.
</p>

<p>
Below is the list of structural classes.
</p>

### :first-child
<p>
It represents the element that is prior to its siblings in a tree structure.
</p>

```css
<style>
table tr:first-child{
 background-color:gray;
}
</style>
```

<br>

### :nth-child(n)
<p>
This class applies CSS properties to those elements that appear at the position evaluated by the resultant of an expression. The expression evaluates to a value resulting in the position of the element in a tree structure.

For example, :nth-child(2n+1) pseudo class applies to the rows of table that appear at the position of the given expression.

tr:nth-child(2n+1) represents rows such as 1th, 3th, 5th, 7th.... for n >= 0.
</p>

```css
<style>
table tr:nth-child(2n+1){
 background-color:gray;
}
</style>
```
<br>

### :last-child
<p>
This pseudo class represents the element that is at the end of its siblings in a tree structure.
</p>

```css
<style>
ul li:last-child{
 background-color:lightblue;
}
</style>
```

<br>

### :nth-last-child(n)
<p>
:nth-last-child(Expression) is the same as :nth-child(Expression) but positioning of elements starts from the end.

tr:nth-last-child(2n+1) represents last row, 3th last row, 5th last row, etc, element.
</p>

```css
<style>
table tr:nth-last-child(2n+1){
 background-color:lightblue;
}
</style>
```

<br>

### :only:child
<p>
It represents the element that is a sole child of the parent element and there is no other sibling.
</p>

```css
<style>
div p:only-child{
 background-color:lightblue;
}
</style>
```
<p>It means the first and last elements are same.</p>

<br>

### :first-of-type
<p>
There might be more than one type of siblings under a common parent. It selects the first element of the one type of sibling.
</p>

```css
<style>
dl dd:first-of-type{
 background-color:lightblue;
}
</style>
```

<p>In the above example, there are two types of siblings i.e. dd and dt. And we choose the <dl> element to apply the CSS properties. It is the same as :nth-child(1).</p>

<br>

### :nth-of-type(n)
<p>
There may be more than one elements of the same type under a common parent. :nth-of-type(Expression) represents those elements of the same type at the position evaluated by the Expression.
</p>

```css
<style>
tr td:nth-of-type(2n+1){
 background-color:gray;
}
tr td:nth-of-type(2n){
 background-color:lightblue;
}
</style>
```

<br>

### :last-of-type
<p>:last-of-type represents the last element in the list of same type of siblings.</p>

```css
<style>
dl dd:last-of-type{
 background-color:lightblue;
}
</style>
```

<br>

### :nth-last-of-type(n)
<p>It is the same as :nth-of-type(n) but it starts counting of position from the end instead of start.</p>

```css
<style>
body > h2:nth-last-of-type(n+6){
 color:blue;
}
</style>
```
<p>It means that the color of all h2 elements is blue except the last five elements.</p>

<br>

---
# Common Css Styling Classes:
<p>
We can style our element using the class selector and define its style properties in it. basic syntax of using css by class selector is following. 
</p>

```css
.class_name { style properties }
```

<p>We have some common style properties in css styling classes like background-color, color, padding, margin, font-size, text-align, border etc.

Below is an example that shows how can we use these styling in our classes
</p>

## Example:

<p>Let's say we have a div element with the class name of fancy.</p>

```css
.fancy{
    background-color: #354783;
    color: #ffffff;
    padding: 5px;
    margin: 10px;
    font-size: 50px;
    text-align: center;
    border: 1px solid;
}
```

<br>

---
# CSS Specificty
<p>
Every selector in CSS has a specificity weight. A selector’s specificity weight, along with its placement in the cascade, identifies how its styles will be rendered.

The type selector has the lowest specificity weight and holds a point value of 0-0-1. The class selector has a medium specificity weight and holds a point value of 0-1-0. Lastly, the ID selector has a high specificity weight and holds a point value of 1-0-0. As we can see, specificity points are calculated using three columns. The first column counts ID selectors, the second column counts class selectors, and the third column counts type selectors.

What’s important to note here is that the ID selector has a higher specificity weight than the class selector, and the class selector has a higher specificity weight than the type selector.

The higher the specificity weight of a selector, the more superiority the selector is given when a styling conflict occurs.
</p>

### Example:

```html
<p id="food">...</p>

```

```css
#food {
background: green;

}
p {
  background: orange;
}
```

<p>Here the id selector has more specific weight than type selector, so the background color will be rendered as green.</p>

<br>

## Specificity Within Combined Selectors

### Example:

```html
<div class="hotdog">
  <p>...</p>
  <p>...</p>
  <p class="mustard">...</p>
</div>
```

```css
.hotdog p {
  background: brown;
}
.hotdog p.mustard {
  background: yellow;
}
```

<p>
Looking at our combined selectors from before, the first selector, .hotdog p, had both a class selector and a type selector. Knowing that the point value of a class selector is 0-1-0 and the point value of a type selector is 0-0-1, the total combined point value would be 0-1-1, found by adding up each kind of selector.

The second selector, .hotdog p.mustard, had two class selectors and one type selector. Combined, the selector has a specificity point value of 0-2-1. The 0 in the first column is for zero ID selectors, the 2 in the second column is for two class selectors, and the 1 in the last column is for one type selector.

Comparing the two selectors, the second selector, with its two classes, has a noticeably higher specificity weight and point value.
</p>

<br>

---
 # CSS Responsive Queries
 <p>
 Css introduced media queries to write responsive design. Based on the device i.e mobile,
 tablet and desktop, the elements show changes its position on the page, changing the fonts, display something extra on the screen.

 It uses the @media rule to include a block of CSS properties only if a certain condition is true. 
 </p>

 ### Example:

 <p>If the browser window is 600px or smaller, the background color will be lightblue:
</p>

```css
@media only screen and (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```

### Add a breakpoint:
<p>Media queries can help with that. We can add a breakpoint where certain parts of the design will behave differently on each side of the breakpoint.

Adding a breakpoint of 768px.
</p>

### Example:

<p>When the screen (browser window) gets smaller than 768px, each column should have a width of 100%:
</p>

```css
/* For desktop: */
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}

@media only screen and (max-width: 768px) {
  /* For mobile phones: */
  [class*="col-"] {
    width: 100%;
  }
}
```

### Always design for mobile first:
<p>Mobile First means designing for mobile before designing for desktop or any other device (This will make the page display faster on smaller devices).

This means that we must make some changes in our CSS.

Instead of changing styles when the width gets smaller than 768px, we should change the design when the width gets larger than 768px. This will make our design Mobile First:</p>

### Example:

```css
/* For mobile phones: */
[class*="col-"] {
  width: 100%;
}

@media only screen and (min-width: 768px) {
  /* For desktop: */
  .col-1 {width: 8.33%;}
  .col-2 {width: 16.66%;}
  .col-3 {width: 25%;}
  .col-4 {width: 33.33%;}
  .col-5 {width: 41.66%;}
  .col-6 {width: 50%;}
  .col-7 {width: 58.33%;}
  .col-8 {width: 66.66%;}
  .col-9 {width: 75%;}
  .col-10 {width: 83.33%;}
  .col-11 {width: 91.66%;}
  .col-12 {width: 100%;}
}
```

<p>We can add as many breakpoints as we like.</p>

### Typical Device Breakpoints:

```
/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {...}

/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {...}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {...}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {...}

/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {...}
```

<br>

---
# Flexbox:
<p>
The Flexible Box Module, usually referred to as flexbox, was designed as a one-dimensional layout model, and as a method that could offer space distribution between items in an interface and powerful alignment capabilities. This article gives an outline of the main features of flexbox, which we will be exploring in more detail in the rest of these guides.
</p>

<br>

## CSS Flex Container:
<p>The flex container becomes flexible by setting the display property to flex:</p>

```css
.flex-container {
  display: flex;
}
```
### Flex container properties:

#### flex-direction:
<p>
The flex-direction property defines in which direction the container wants to stack the flex items.
</p>

```css
/* The column value stacks the flex items vertically (from top to bottom) */

.flex-container {
  display: flex;
  flex-direction: column;
}
```

```css
/* The column-reverse value stacks the flex items vertically (but from bottom to top) */

.flex-container {
  display: flex;
  flex-direction: column-reverse;
}
```

```css
/* The row value stacks the flex items horizontally (from left to right) */

.flex-container {
  display: flex;
  flex-direction: row;
}
```

```css
/* The row-reverse value stacks the flex items horizontally (but from right to left) */

.flex-container {
  display: flex;
  flex-direction: row-reverse;
}
```

#### The flex-wrap Property:
<p>The flex-wrap property specifies whether the flex items should wrap or not.</p>

```css
/* The wrap value specifies that the flex items will wrap if necessary. */

.flex-container {
  display: flex;
  flex-wrap: wrap;
}
```
```css
/* The nowrap value specifies that the flex items will not wrap (this is default)*/

.flex-container {
  display: flex;
  flex-wrap: nowrap;
}
```
```css
/* The wrap-reverse value specifies that the flexible items will wrap if necessary, in reverse order. */

.flex-container {
  display: flex;
  flex-wrap: wrap-reverse;
}
```

#### The flex-flow Property:
<p>The flex-flow property is a shorthand property for setting both the flex-direction and flex-wrap properties.</p>

```css
.flex-container {
  display: flex;
  flex-flow: row wrap;
}
```

#### The justify-content Property:
<p>The justify-content property is used to align the flex items.</p>

```css
/* The center value aligns the flex items at the center of the container.*/

.flex-container {
  display: flex;
  justify-content: center;
}
```

```css
/* The flex-start value aligns the flex items at the beginning of the container (this is default).*/

.flex-container {
  display: flex;
  justify-content: flex-start;
}
```

```css
/* The flex-end value aligns the flex items at the end of the container.*/

.flex-container {
  display: flex;
  justify-content: flex-end;
}
```

```css
/* The space-around value displays the flex items with space before, between, and after the lines.*/

.flex-container {
  display: flex;
  justify-content: space-around;
}
```

```css
/*The space-between value displays the flex items with space between the lines.*/

.flex-container {
  display: flex;
  justify-content: space-between;
}
```

#### The align-items Property:
<p> The align-items property is used to align the flex items.</p>

```css
/*The center value aligns the flex items in the middle of the container.*/

.flex-container {
  display: flex;
  height: 200px;
  align-items: center;
}
```

```css
/*The center value aligns the flex items in the middle of the container.*/

.flex-container {
  display: flex;
  height: 200px;
  align-items: center;
}
```

```css
/*The flex-end value aligns the flex items at the bottom of the container.*/

.flex-container {
  display: flex;
  height: 200px;
  align-items: flex-end;
}
```

```css
/* The stretch value stretches the flex items to fill the container (this is default) */

.flex-container {
  display: flex;
  height: 200px;
  align-items: stretch;
}
```

```css
/* The baseline value aligns the flex items such as their baselines aligns*/

.flex-container {
  display: flex;
  height: 200px;
  align-items: baseline;
}
```

#### The align-content Property:
<p>The align-content property is used to align the flex lines.</p>

```css
/* The space-between value displays the flex lines with equal space between them */

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: space-between;
}
```

```css
/* The space-around value displays the flex lines with space before, between, and after them. */

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: space-around;
}
```

```css
/* The stretch value stretches the flex lines to take up the remaining space (this is default) */

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: stretch;
}
```

```css
/* The center value displays display the flex lines in the middle of the container. */

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: center;
}
```

```css
/* The flex-start value displays the flex lines at the start of the container. */

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: flex-start;
}
```

```css
/* The flex-end value displays the flex lines at the end of the container. */ 

.flex-container {
  display: flex;
  height: 600px;
  flex-wrap: wrap;
  align-content: flex-end;
}
```

<br>

## Flex Items Property:

#### The order Property:
<p>The order property specifies the order of the flex items.</p>

```css
/*The order property can change the order of the flex items.*/

<div class="flex-container">
  <div style="order: 3">1</div>
  <div style="order: 2">2</div>
  <div style="order: 4">3</div>
  <div style="order: 1">4</div>
</div>
```

#### The flex-grow Property:
<p>
The flex-grow property specifies how much a flex item will grow relative to the rest of the flex items.
</p>

```css
/* Make the third flex item grow eight times faster than the other flex items. */

<div class="flex-container">
  <div style="flex-grow: 1">1</div>
  <div style="flex-grow: 1">2</div>
  <div style="flex-grow: 8">3</div>
</div>
```

#### The flex-shrink Property:
<p>The flex-shrink property specifies how much a flex item will shrink relative to the rest of the flex items.</p>

```css
/*Do not let the third flex item shrink as much as the other flex items.*/

<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex-shrink: 0">3</div>
  <div>4</div>
</div>
```

#### The flex-basis Property:
<p>The flex-basis property specifies the initial length of a flex item.</p>

```css
/*Set the initial length of the third flex item to 200 pixels.*/

<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex-basis: 200px">3</div>
  <div>4</div>
</div>
```

#### The flex Property:
<p>The flex property is a shorthand property for the flex-grow, flex-shrink, and flex-basis properties.</p>

```css
/*Make the third flex item not growable (0), not shrinkable (0), and with an initial length of 200 pixels.*/

<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex: 0 0 200px">3</div>
  <div>4</div>
</div>
```

<br>

---

# GRID
<p>The CSS Grid Layout Module offers a grid-based layout system, with rows and columns, making it easier to design web pages without having to use floats and positioning.</p>

## Display Property:
<p>
An HTML element becomes a grid container when its display property is set to grid or inline-grid.
</p>

<p>All direct children of the grid container automatically become grid items.
</p>

```css
.grid-container {
  display: grid;
}
```

```css
.grid-container {
  display: inline-grid;
}
```

### Grid columns:
<p>The vertical lines of grid items are called columns.</p>

<br>

### Grid rows:
<p>The vertical lines of grid items are called columns.</p>

<br>

### Grid gaps:
<p>The spaces between each column/row are called gaps.</p>

```css
/*The grid-column-gap property sets the gap between the columns.*/

.grid-container {
  display: grid;
  grid-column-gap: 50px;
}
```

```css
/*The grid-row-gap property sets the gap between the rows.*/

.grid-container {
  display: grid;
  grid-row-gap: 50px;
}
```

```css
/*The grid-gap property is a shorthand property for the grid-row-gap and the grid-column-gap properties.*/

.grid-container {
  display: grid;
  grid-gap: 50px 100px;
}
```

```css
/*The grid-gap property can also be used to set both the row gap and the column gap in one value.*/

.grid-container {
  display: grid;
  grid-gap: 50px;
}
```

<br>

### Grid lines:

<p>The lines between columns are called column lines.

The lines between rows are called row lines.</p>

```css
/*Place a grid item at column line 1, and let it end on column line 3.*/

.item1 {
  grid-column-start: 1;
  grid-column-end: 3;
}
```

```css
/*Place a grid item at row line 1, and let it end on row line 3.*/

.item1 {
  grid-row-start: 1;
  grid-row-end: 3;
}
```

<br>

## CSS Grid Container

### Grid Template Column Property:
<p>
The grid-template-columns property defines the number of columns in your grid layout, and it can define the width of each column.
</p>

```css
/* Set a size for the 4 columns. */
.grid-container {
  display: grid;
  grid-template-columns: 80px 200px auto 40px;
}
```

### Grid Template Row Property:
<p>The grid-template-rows property defines the height of each row.</p>

```css
/* Set a size for the 2 rows. */
.grid-container {
  display: grid;
  grid-template-rows: 80px 200px;
}
```

### The justify-content Property:
<p>The justify-content property is used to align the whole grid inside the container.</p>

```css
.grid-container {
display: grid;
justify-content: space-evenly;
}
```

### The align-content Property:
<p>The align-content property is used to vertically align the whole grid inside the container.</p>

```css
.grid-container {
  display: grid;
  height: 400px;
  align-content: center;
}
```

<br>

## CSS Grid Item

### Grid Column Property:
<p>
The grid-column property defines on which column(s) to place an item.
</p>

```css
/* Make "item1" start on column 1 and end before column 5.*/

.item1 {
  grid-column: 1 / 5;
}
```

```css
/* Make "item1" start on column 1 and span 3 columns. */

.item1 {
  grid-column: 1 / span 3;
}
```

### Grid Row Property:
<p>The grid-row property defines on which row to place an item.</p>

```css
/* Make "item1" start on row-line 1 and end on row-line 4. */

.item1 {
  grid-row: 1 / 4;
}
```

```css
/* Make "item1" start on row 1 and span 2 rows.*/

.item1 {
  grid-row: 1 / span 2;
}
```

### Grid Area property:
<p>
The grid-area property can be used as a shorthand property for the grid-row-start, grid-column-start, grid-row-end and the grid-column-end properties.
</p>

```css
/*Make "item8" start on row-line 1 and column-line 2, and end on row-line 5 and column line 6. */

.item8 {
  grid-area: 1 / 2 / 5 / 6;
}
```

```css
/*Make "item8" start on row-line 2 and column-line 1, and span 2 rows and 3 columns.*/

.item8 {
  grid-area: 2 / 1 / span 2 / span 3;
}
```

<br>

---

## HTML

* Inline vs Block Elements.
* Common header meta tags

## Inline vs Block Elements

### Block Elements:
<p>A block-level element always starts on a new line.

A block-level element always takes up the full width available (stretches out to the left and right as far as it can).

A block level element has a top and a bottom margin, whereas an inline element does not.</p>

#### Example of block-level elements:

```html
<address> 
<article> 
<aside>
<blockquote>
<canvas>
<dd>
<div>
<dl>
<dt>
<fieldset>
<figcaption>
<figure>
<footer>
<form>
<h1>-<h6>
<header>
<hr>
<li>
<main>
<nav>
<noscript>
<ol>
<p>
<pre>
<section>
<table>
<tfoot>
<ul>
<video>
```

### Inline Elements:
<p>An inline element does not start on a new line.

An inline element only takes up as much width as necessary.
</p>

#### Example of inline-level elements:

```html
<a>
<abbr>
<acronym>
<b>
<bdo>
<big>
<br>
<button>
<cite>
<code>
<dfn>
<em>
<i>
<img>
<input>
<kbd>
<label>
<map>
<object>
<output>
<q>
<samp>
<script>
<select>
<small>
<span>
<strong>
<sub>
<sup>
<textarea>
<time>
<tt>
<var>
```

<br>

---

# Header Meta Tags

## Head Tag:
<p>
The head tag in HTML is used to define the head portion of the document which contains information related to the document. 
The head tag contains other head elements such as title, meta, link, style etc.
</p>

### Example:

```html
Set the title for page
<title>Web Page</title>
```

## Meta Tag:
<p>
The meta tag defines metadata about an HTML document. Metadata is data (information) about data.

Meta tags always go inside the head element, and are typically used to specify character set, page description, keywords, author of the document, and viewport settings.

Metadata will not be displayed on the page, but is machine parsable.

Metadata is used by browsers (how to display content or reload page), search engines (keywords), and other web services.

There is a method to let web designers take control over the viewport (the user's visible area of a web page), through the meta tag (See "Setting The Viewport" example below).
</p>

### Examples:

```html
Define keywords for search engines.

<meta name="keywords" content="HTML, CSS, JavaScript">
```

```html
Define a description of your web page:

<meta name="description" content="Free Web tutorials for HTML and CSS">
```

```html
Define the author of a page:

<meta name="author" content="Gaurav Tiwari">
```

```html
Refresh document every 30 seconds:

<meta http-equiv="refresh" content="30">
```

```html
Setting the viewport to make your website look good on all devices:

<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

```html
Specify the character encoding for the HTML document:

<meta charset="UTF-8">
```

<br>

---

# REFERENCES:

* https://learn.shayhowe.com/html-css/opening-the-box-model/
* https://www.w3schools.com/css/css_positioning.asp
* https://www.web4college.com/css/web4-css-structural-classes.php
* https://www.w3schools.com/css/css_rwd_mediaqueries.asp
* https://www.w3schools.com/css/css3_flexbox_container.asp
* https://www.w3schools.com/css/css3_flexbox_items.asp
* https://www.w3schools.com/html/html_blocks.asp
* https://www.w3schools.com/tags/tag_meta.asp
