# CSS

## 1. **How to add comments on CSS?**

To comment in CSS, place your plain text inside `\* */`
 marks. This tells the browser that they are notes and should not be rendered on the front end.

## 2. **Why do we use pseudo-class?**

CSS pseudo-classes are used to add special effects to some selectors.

```
selector:pseudo-class {
  property: value;
}
```

example:

```
div:hover {
  background-color: blue;
}
```

## 3. **How is specificity applied?**

If there are two or more CSS rules that point to the same element, 
the selector with the highest specificity value will "win", and its 
style declaration will be applied to that HTML element.

Think of specificity as a score/rank that determines which style declaration are ultimately applied to an element.

The amount of specificity a selector has is measured using four 
different values (or components), which can be thought of as thousands, 
hundreds, tens, and ones — four single digits in four columns:

- 1000 - Inline/Style Tag
- Hundreds - One for each ID Selector
- Tens - One for each class selector, attribute selector, or pseudo-class contained inside the overall selector.
- Ones - One for each element selector, pseudo-element contained inside the overall selector.

Note: Universal selector (*), combinators (+, >, ~, ' ') and negation pseudo-class (:not) have no effect on specificity.

```
| Selector                                | Thousands | Hundreds | Tens | Ones | Total |
| --------------------------------------- | --------- | -------- | ---- | ---- | ----- |
| h1                                      | 0         | 0        | 0    | 1    | 0001  |
| h1 + p                                  | 0         | 0        | 0    | 2    | 0002  |
| h1 + p::first-letter                    | 0         | 0        | 0    | 3    | 0003  |
| li > a[href*="en-US"] > .inline-warning | 0         | 0        | 2    | 2    | 0022  |
| .class1                                 | 0         | 0        | 1    | 0    | 0010  |
| ul.class1                               | 0         | 0        | 1    | 1    | 0011  |
| #id1                                    | 0         | 1        | 0    | 0    | 0100  |
| style                                   | 1         | 0        | 0    | 0    | 1000  |

```

## 4. **What method allows an element to be moved from its current position?**

The translate() method moves an element from its current position 
(according to the parameters given for the X-axis and the Y-axis).

Take a look at this example for a better understanding.

[EXAMPLE](https://codepen.io/abdul-from-masai/pen/zYpRJaE)

## 5. **What properties does the flex model have?**

### Properties for the parent (flex-container):

### display

This defines a flex container; inline or block depending on the given
 value. It enables a flex context for all its direct children.

```
.container {
  display: flex; /* or inline-flex */
}

```

### flex-direction

The flex-direction property defines in which direction the container 
wants to stack the flex items. Flexbox is a single-direction layout 
concept. Think of flex items as primarily laying out either in 
horizontal rows or vertical columns.

```
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}

```

- row (default): left to right
- row-reverse: the right to left
- column: same as row but top to bottom
- column-reverse: same as row-reverse but bottom to top

![image](https://drive.google.com/uc?id=1q2Py_TnfBn65EptlUBzFzXATEZ0CJrsA)


### flex-wrap

By default, flex items will all try to fit onto one line. You can 
change that and allow the items to wrap as needed with this property.

```
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}

```

- nowrap (default): all flex items will be on one line
- wrap: flex items will wrap onto multiple lines, from top to bottom.
- wrap-reverse: flex items will wrap onto multiple lines from bottom to top.

![image](https://drive.google.com/uc?id=1xad8OL4BDq3cMMS5_UgvPKdGyKVPP3Ds)

### flex-flow

This is a shorthand for the flex-direction and flex-wrap properties, 
which together define the flex container’s main and cross axes. The 
default value is row nowrap.

```
.container {
  flex-flow: column wrap;
}

```

### justify-content

The justify-content property is used to align the flex items along the main axis;

```
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right;
}

```

- flex-start (default): items are packed toward the start of the flex-direction.
- flex-end: items are packed toward the end of the flex-direction.
- start: items are packed toward the start of the writing-mode direction.
- end: items are packed toward the end of the writing-mode direction.
- left: items are packed toward the left edge of the container unless
that doesn’t make sense with the flex-direction, then it behaves like
a start.
- right: items are packed toward the right edge of the container, unless
that doesn’t make sense with the flex-direction, then it behaves like
an end.
- center: items are centered along the line
- space-between: items are evenly distributed in the line; the first item is on the start line, last item on the end line
- space-around: items are evenly distributed in the line with equal
space around them. Note that visually the spaces aren’t equal, since all the items have equal space on both sides. The first item will have one
unit of space against the container edge, but two units of space between the next item because that next item has its own spacing that applies.
- space-evenly: items are distributed so that the spacing between any two items (and the space to the edges) is equal.

PS: The safest values are flex-start, flex-end, and center. (as some of the properties never got support from the browser)

![image](https://drive.google.com/uc?id=1m398W6NoMJzG_uB9OAMERbXYxxNfuvkj)

### align-items

The align-items property is used to align the flex items along the cross axis.

```
.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end;
}

```

- stretch (default): The stretch value stretches the flex items to fill the container (this is the default):
- flex-start / start / self-start: items are placed at the start of the cross axis.
- flex-end / end / self-end: items are placed at the end of the cross axis.
- center: The center value aligns the flex items in the middle of the container
- baseline: items are aligned such as their baselines align

![image](https://drive.google.com/uc?id=1nk0YAW2WMp1HfqqIj8KEPZPAfg7qSU3X)

### align-content

This aligns a flex container’s lines within when there is extra space
 in the cross-axis, similar to how justify-content aligns individual 
items within the main-axis.

Note : This property only takes effect on multi-line flexible 
containers, where flex-wrap is set to either wrap or wrap-reverse).

```
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch ;
}

```

- flex-start: items packed to the start of the container
- flex-end: items packed to the end of the container.
- center: items centered in the container
- space-between: items evenly distributed; the first line is at the start of the container while the last one is at the end
- space-around: items evenly distributed with equal space around each line
- space-evenly: items are evenly distributed with equal space around them
- stretch: lines stretch to take up the remaining space

![image](https://drive.google.com/uc?id=1XtXeE1Pl27Hv6-sgHCz2X6QKazcnrjob)

### gap, row gap, column gap

The gap property explicitly controls the space between flex items. It
 applies that spacing only between items not on the outer edges.

```
.container {
  display: flex;
  ...
  gap: 10px;
  gap: 10px 20px; /* row-gap column gap */
  row-gap: 10px;
  column-gap: 20px;
}

```

![image](https://drive.google.com/uc?id=1uQhMlPcV1fqEYD65d1nBjxFAdh6hNhVU)

---

### Properties for the children (flex-items);

### order

The order property can change the order of the flex items:

```
<div class="flex-container">
  <div style="order: 3">1</div>
  <div style="order: 2">2</div>
  <div style="order: 4">3</div>
  <div style="order: 1">4</div>
</div>

```

will give

![image](https://drive.google.com/uc?id=1BIBY_yYRble8N78cXIJX0pNUMfh0uFa0)

### flex-grow

The flex-grow property specifies how much a flex item will grow relative to the rest of the flex items.

```
<div class="flex-container">
  <div style="flex-grow: 1">1</div>
  <div style="flex-grow: 1">2</div>
  <div style="flex-grow: 8">3</div> // Make the third flex item grow eight times faster than the other flex items:
</div>

```

![image](https://drive.google.com/uc?id=1zDjsnQpCoQ_1N5Dj7iLr4y5Eqtk8nY3A)

### flex-shrink

The flex-shrink property specifies how much a flex item will shrink relative to the rest of the flex items.

```
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex-shrink: 0">3</div> //Do not let the third flex item shrink as much as the other flex items:
  <div>4</div>
  <div>5</div>
  <div>6</div>
  <div>7</div>
  <div>8</div>
  <div>9</div>
  <div>10</div>
</div>

```

will give

![image](https://drive.google.com/uc?id=1wzAqvNjzwLFSJ7kal_ZoUcnTXGID_PSC)

### flex-basis

The flex-basis property specifies the initial length of a flex item before the remaining space is distributed.

```
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex-basis: 200px">3</div> // Set the initial length of the third flex item to 200 pixels:
  <div>4</div>
</div>

```

will give

![image](https://drive.google.com/uc?id=1o-Ifa6yEA9bk27sv8BNJDHgnvRejes6w)

### flex

The flex property is a shorthand property for the flex-grow, flex-shrink, and flex-basis properties.

```
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="flex: 0 0 200px">3</div> // Make the third flex item not growable (0), not shrinkable (0), and with an initial length of 200 pixels:
  <div>4</div>
</div>

```

### align-self

- The align-self property specifies the alignment for the selected item inside the flexible container.
- The align-self property overrides the default alignment set by the container's align-items property.

```
<html>
<head>
<style>
.flex-container {
  display: flex;
  height: 200px;
  background-color: #f1f1f1;
}

.flex-container > div {
  background-color: DodgerBlue;
  color: white;
  width: 100px;
  margin: 10px;
  text-align: center;
  line-height: 75px;
  font-size: 30px;
}
</style>
</head>
<body>

<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div style="align-self: center">3</div>
  <div>4</div>
</div>

</body>
</html>

```

will give the following

![image](https://drive.google.com/uc?id=1e9416Cmit_x4sXzWBZLkFJ4QFrdUd8ji)

## 

## 6. **What is the difference between flex and grids?**

- Grid is made for a two-dimensional layout while Flexbox is for one.
This means Flexbox can work on either row or columns at a time, but
Grids can work on both.
- Major Uniqueness between Flexbox and Grids is that the former works on content while the latter is based on the layout.
- CSS Grids help you create the outer layout of the webpage. You can
build complex as well as responsive designs with this. This is why it is
called ‘layout first’. Flexbox mostly helps align content & move
blocks.

## 7. Give an example where you cannot use flexbox, and you can only use grids?

- Grid is usually used to make a more complex layout. You can build
complex as well as responsive designs with this. It works with both rows and columns. Flexbox works better in one dimension only (either rows OR
columns).
- Now take a look at this example;

(https://codepen.io/abdul-from-masai/pen/KKZQYgw)

- If you have some complex layout like this wherein you want to layout in different ways basis the screen size; You'd rather use CSS grid over
flex;
- for a simple one-dimensional layout flexbox can be useful to help align content

## 8. What are combinators? give examples of how you can use them

- Combinators let you combine two or more selectors so you can be
more specific in your selection method. There are different types of
combinators.

```
.
,
+
~
>
space

```

### Type & Class (.)

```
elemtype.class { style properties }

```

```
<div>This is the first div</div>
<div class="class1">This is the second div</div>
<div class="class2">This is the third div</div>
<p>This is the first paragraph</p>
<p class="class1">This is the second paragraph</p>
<p class="class2">This is the third paragraph</p>

```

```
/* All <div> elements */
div {
  color: red;
}

/_ All elements with class="class1" _/
.class1 {
color: green;
}

/_ All <p> elements with class="class2" _/
p.class2 {
color: violet;
}

```

Ref: [LINK](https://codepen.io/nrupuld/pen/zVweGK)

### Multiple Selectors, Same Properties (,)

The comma in a CSS selector separates multiple selectors within the same styles.

```
selector1, selector2 { style properties }

```

```
div, p {
  padding: 10px;
  font-size: 20px;
  margin: 0;
}

```

Ref : [LINK](https://codepen.io/nrupuld/pen/xopQEZ)

### Adjacent Sibling Selector (+)

The adjacent sibling combinator (+) separates two selectors and 
matches the second element only if it immediately follows the first 
element, and both are children of the same parent element.

```
former_element + target_element { style properties }

```

Ref: [LINK](https://codepen.io/nrupuld/pen/XLVyzm)

### General Sibling Selector (~)

The general sibling combinator (~) separates two selectors and 
matches the second element only if it follows the first element (though 
not necessarily immediately), and both are children of the same parent

```
former_element ~ target_element { style properties }

```

Ref: [LINK](https://codepen.io/nrupuld/pen/pXpQLM)

### Child Combinator (>)

The child combinator (>) is placed between two CSS selectors. It 
matches only those elements matched by the second selector that are the 
children of elements matched by the first.

```
selector1 > selector2 { style properties }

```

Ref : [LINK](https://codepen.io/nrupuld/pen/rEpQRL)

### Descendant Combinator ( )

The descendant combinator is typically represented by a single space ( )
 character combines two selectors such that elements matched by the 
second selectors are selected if they have an ancestor element matching 
the first selector.

```
selector1 selector2 { style properties }

```

Ref: [LINK](https://codepen.io/nrupuld/pen/Oezaed)

## 9. What does object-fit do?

The CSS object-fit property is used to specify how an `<img>` or `<video>` should be resized to fit its container.

This property tells the content to fill the container in a variety of
 ways; such as "preserve that aspect ratio" or "stretch up and take up 
as much space as possible".

You can read more about it here.

-[Ref.](https://developer.mozilla.org/en-US/docs/Web/CSS/object-fit)
-[Ref.](https://www.w3schools.com/css/css3_object-fit.asp)

## 10. What does rotate do?

The transform property applies a 2D or 3D transformation to an 
element. This property allows you to rotate, scale, move, skew, etc., 
elements.

```
rotate(angle) // Defines a 2D rotation, the angle is specified in the parameter

```

- You can give it a try here: Defines a 2D rotation, the angle is specified in the parameter
- For More Info Ref: [LINK](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate)

## 11. What rule can be used to define animations

- The @keyframes rule specifies the animation code.
- The animation is created by gradually changing from one set of CSS styles to another.
- During the animation, you can change the set of CSS styles many times.
- Specify when the style change will happen in percent or with the
keywords "from" and "to", which is the same as 0% and 100%. 0% is the
beginning of the animation, and 100% is when the animation is complete.

Syntax :

```
@keyframes animationname {keyframes-selector {css-styles;}}

```

Take a look at the following example.

For More info :
[LINK 1](https://www.w3schools.com/cssref/css3_pr_animation-keyframes.asp)[LINK 2](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)

## 12. When working with attribute selectors, how can you select elements which contain a particular attribute value?

```
a[href*="en-US"] // selects an `a` tag which a particular href attribute value that has been asked

```

## 13. What does @media do?

- The @media rule is used in media queries to apply different styles for different media types/devices.
- Media queries can be used to check many things, such as:
    - width and height of the viewport
    - width and height of the device
    - orientation (is the tablet/phone in landscape or portrait mode?)
    - resolution
- Using media queries are a popular technique for delivering a tailored style sheet (responsive web design) to desktops, laptops, tablets, and
mobile phones.
- You can also use media queries to specify that certain styles are
only for printed documents or for screen readers (mediatype: print,
screen, or speech).
- In addition to media types, there are also media features. Media
features provide more specific details to media queries, by allowing to
test for a specific feature of the user agent or display device. For
example, you can apply styles to only those screens that are greater, or smaller, than a certain width.

syntax :

```
body {
  background-color: lightblue;
}

@media screen and (min-width: 400px) {
  body {
    background-color: lightgreen;
  }
}

@media screen and (min-width: 800px) {
  body {
    background-color: lavender;
  }
}

```

## 14. What can be used to override properties of an element

- To override the CSS properties of a class using another class, we can use the`! important` directive. In CSS, `!important` means “this is important”, and the `property: value` pair that has this directive is always applied even if the other element has higher specificity.

Syntax :

```
element1 {
    property-x: value_y  !important; /* This will be applied. */
}
element2 {
    property-x: value_z; /* This will not be applied. */
}

```

```
html :
 <p class="my_fav_font my_para">Cascading Style Sheets,fondly referred to as CSS, is a..</p>

css :
.my_fav_font {
  font-family: 'Indie Flower', cursive !important;
  /* This will be applied. */
}

.my_para {
  font-family: 'Mansalva', cursive;
  /* This will not be applied. */
  text-align: justify;
  background-color: powderblue;
  font-size: 130%;
}

```

## 15. How can you select every alternate element in a list of elements using CSS?

Syntax :

HTML

```
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
  <li>5</li>
  <li>6</li>
  <li>7</li>
  <li>8</li>
  <li>9</li>
  <li>10</li>
</ul>

```

CSS

```
ul{
  list-style-type: none;
  color: white;
}
li:nth-of-type(odd){ // or you can also use li:nth-child(odd)
  background-color:blue;
}
li:nth-of-type(even){
  background-color:red;
}

```

## 16. What is the ranking of selectors with respect to specificity

Ranking from Low To High

- universal_selector, combinators selector, negation pseudo-class
(: not) selector ( these selectors have no effects on specificity )
- element selector, pseudo element selector
- class selector, attribute selector, pseudo-class contained inside the overall selector
- id selector
- inline styling

## 17. How can we apply the same styles to multiple selectors?

- To group CSS selectors in a style sheet, use commas to separate
multiple grouped selectors in the style. In this example, the style
affects the p and div elements:

```
div, p { color: #f00; }

```

## 18. What are the differences between relative and absolute in CSS?

| Relative      | Absolute |
| ----------- | ----------- |
| An element with position: relative; is positioned relative to its normal position.      | An element with position: absolute; is positioned relative to the nearest positioned ancestor. However; if an absolute positioned element has no positioned ancestors, it uses the document body, and moves along with page scrolling.       |
| Setting the top, right, bottom, and left properties of a relatively-positioned element will cause it to be adjusted away from its normal position. Other content will not be adjusted to fit into any gap left by the element.   | Absolute positioned elements are removed from the normal flow, and can overlap elements.   
|example : https://www.w3schools.com/css/tryit.asp?filename=trycss_position_relative   |  example: https://www.w3schools.com/css/tryit.asp?filename=trycss_position_absolute






