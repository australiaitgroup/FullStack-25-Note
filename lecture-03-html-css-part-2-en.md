# Lecture03 HTML & CSS - Part 2

> This note is based on the lecture ([link](https://jiangren.com.au/study/lesson?programId=672448ecea33cf003687af93&lessonId=673c41cb0022bb00124fe2ed&tab=content) by Ally Tang. The entire lecture is about CSS (**Cascading Style Sheets**). If doubts, please ask anyone or consult the documentation [W3School](https://www.w3schools.com/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML). Happy Coding



## TOC

- [CSS - Cascading Style Sheets](#css---cascading-style-sheets)
 - [Introduction](#introduction)
   - [What does CSS do?](#what-does-css-do)
   - [Emmet](#emmet)
   - [How to Add CSS into HTML](#how-to-add-css-into-html)
     - [Inline CSS](#inline-css)
     - [Internal CSS](#internal-css)
     - [External CSS](#external-css)
 - [CSS Selectors](#css-selectors)
   - [Tag Name (element selector)](#tag-name-element-selector)
   - [Class Selector](#class-selector)
   - [ID Selector](#id-selector)
   - [Advanced CSS Selectors](#advanced-css-selectors)
     - [Wildcard Selector](#wildcard-selector)
     - [Group Selector](#group-selector) 
     - [Attribute Selector](#attribute-selector)
     - [Descendant Selector](#descendant-selector)
     - [Child Selector](#child-selector)
     - [General Sibling Selector](#general-sibling-selector)
     - [Adjacent Sibling Selector](#adjacent-sibling-selector)
     - [Combined/Compound Selector](#combinedcompound-selector)
   - [Pseudo-class Selectors for Links](#pseudo-class-selectors-for-links)
   - [Structural Pseudo-class Selectors](#structural-pseudo-class-selectors)
 - [CSS Font and Text Properties](#css-font-and-text-properties)
   - [Font Properties](#font-properties)
   - [Text Properties](#text-properties)
 - [Display Properties: Understanding Block, Inline, and Inline-Block](#display-properties-understanding-block-inline-and-inline-block)
 - [CSS Background Properties: Making Beautiful Backgrounds](#css-background-properties-making-beautiful-backgrounds)
 - [The Three Core Concepts of CSS: Cascading, Inheritance, and Specificity](#the-three-core-concepts-of-css-cascading-inheritance-and-specificity)
   - [Cascading Nature of CSS](#cascading-nature-of-css)
   - [CSS Inheritance](#css-inheritance)
   - [Specificity (Priority Rules)](#specificity-priority-rules)
 - [The CSS Box Model: Building Blocks of Web Layout](#the-css-box-model-building-blocks-of-web-layout)
   - [The Box Model Layers (from inside out)](#the-box-model-layers-from-inside-out)
   - [Padding](#padding)
   - [border](#border)
   - [Margin](#margin)
 - [CSS flexbox](#css-flexbox)
   - [What is flexbox?](#what-is-flexbox)
     - [How to use flexbox?](#how-to-use-flexbox)
   - [Flexbox - two axes : Main and Cross](#flexbox---two-axes--main-and-cross)
   - [Flex Direction: Changing the Flow](#flex-direction-changing-the-flow)
   - [Justify-Content: Arranging Items Along the Main Axis](#justify-content-arranging-items-along-the-main-axis)
   - [Align-Items: Cross Axis Alignment Magic](#align-items-cross-axis-alignment-magic)
   - [Understanding Flex Item Growth and Shrink](#understanding-flex-item-growth-and-shrink)

## CSS - Cascading Style Sheets

### Introduction

Cascading Style Sheets, short for CSS,is a style sheet mechanism (or rules) used to define the presentation and formatting of HTML documents. While not a programming language[^1], CSS is a declarative specification that describes how elements should be rendered on screens, paper, or other media. 


#### What does CSS do?

- Controls the visual presentation of web pages
- Defines styles for your HTML elements (colors, sizes, spacing, etc.)
- Handles page layouts and positioning
- Manages responsive design
- Enables animations and visual effects

![](https://i.imgur.com/HGRISDm.png)

A CSS rule consists of several parts:

1. **Selector** (`h1`): Targets the HTML element(s) you want to style
2. **Declaration Block**: Everything inside the curly braces `{ }`
3. **Declarations**: Individual styling rules inside the block, like `font-size: 12px;`
   - **Property**: The styling feature you want to change (like `color` or `font-size`)
   - **Value**: The setting you want to apply (like `blue` or `12px`)
   - Each declaration ends with a semicolon `;`


```css
h1 {
  color: blue;
  font-size: 12px;
}
```

>This rule:
>- Targets all `<h1>` elements
>- Contains two declarations
>- Uses curly braces `{}` to group the declarations
>- Separates each declaration with a semicolon `;`


How do you make a CSS comment?

One line comment as follows
```css
/* This is a comment */
```

multiple line comment as follows

```css
/*
This is a comment
*/
```

#### Emmet
Ally Tang demonstrated how to use the extension Emmet to write CSS faster. 

Emmet is a powerful toolkit that helps you write HTML and CSS code faster. It's like a shorthand that expands into full code! Emmet can help you increasee your productivity. 

#### How Emmet Works:
For example, if you type:
```
ul>li5
```

Emmet will automatically expand it into:

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

This simple shortcut creates an unordered list with 5 list items - much faster than typing all the tags manually!

> 💡 **Pro Tip**: Most modern code editors like VS Code have Emmet built-in, so you can start using it right away.

Documentation: [VScode Emmet](https://code.visualstudio.com/docs/editor/emmet)


#### How to Add CSS into HTML

There are three ways to add CSS into HTML:

1. Inline CSS: Directly in the HTML element
2. Internal CSS: Inside the `<head>` section of the HTML file
3. External CSS: In a separate CSS file

#### Inline CSS

Inline CSS is the simplest way to add CSS to your HTML. It's done directly within the HTML element using the `style` attribute.

```html
<h1 style="color: blue; font-size: 12px;">Hello World</h1>
```

##### Internal CSS

Internal CSS is placed inside the `<head>` section of the HTML file, using the `<style>` tag.

```html
<head>
  <style>
    h1 { color: blue; font-size: 12px; }
  </style>
</head>
```

##### External CSS

External CSS is stored in a separate `.css` file. This file is linked to the HTML file using the `<link>` tag.

```html
<link rel="stylesheet" href="styles.css">
```

### CSS Selectors

Let's talk about CSS selectors. Since we known that CSS is a style sheet mechanism (or rules) used to define the presentation and formatting of HTML documents. The first thing we need to know is how to select the HTML elements we want to style. As you may be hinted previously, we can style the HTML elements by their tag name, class, or ID. 

#### Tag Name (element selector)

```css
h1 { 
    color: blue; 
    font-size: 12px; 
}
```

#### Class Selector 

```css
.my-class {
    color: blue; 
    font-size: 12px; 
}
```

#### ID Selector

```css
#my-id {
    color: blue; 
    font-size: 12px; 
}
```


#### Advanced CSS Selectors

Special selectors such as wildcard selector, group selector, and attribute selector etc

##### Wildcard Selector

```css
* {
    color: blue; 
    font-size: 12px; 
}
```
this means all elements will be styled.

##### Group Selector

```css
h1, h2, h3 {
    color: blue; 
    font-size: 12px; 
}
```

##### Attribute Selector

```css
[type="text"] {
    color: blue; 
    font-size: 12px; 
}
```

Note: it is common to use class selector to style the HTML elements than using ID selector. 




##### Descendant Selector

```css
.my-class h1 {
    color: blue; 
    font-size: 12px; 
}
```

This selector targets all `<h1>` elements that are descendants of any element with the class `my-class`.

##### Child Selector

```css
.my-class > h1 {
    color: blue; 
    font-size: 12px; 
}
```

This selector targets all `<h1>` elements that are direct children of any element with the class `my-class`.

##### General Sibling Selector

```css
/* Targets ALL <p> elements that follow an <h1> */
h1 ~ p {
    color: blue;
}
```

Example usage:
```html
<div>
    <p>This paragraph is NOT blue (before h1)</p>
    <h1>Title</h1>
    <span>This span is not affected</span>
    <p>This paragraph IS blue</p>
    <div>Something else</div>
    <p>This paragraph IS ALSO blue</p>
</div>



```



##### Adjacent Sibling Selector

The adjacent sibling selector (`+`) targets an element that comes **immediately after** another specific element, when both share the same parent.

```css
/* Targets any <p> that comes immediately after an <h1> */
h1 + p {
    color: blue;
}
```



Example usage:

```html
<div>
    <h1>Title</h1>
    <p>This paragraph IS blue (adjacent to h1)</p>
    <p>This paragraph is NOT blue</p>
</div>

<h1>Another Title</h1>
<span>This span is NOT blue</span>
<p>This paragraph is NOT blue (not adjacent)</p>
```

##### Combined/Compound Selector

A combined selector targets elements that match ALL the specified selectors at once. It's written by joining selectors together without any space between them.

```css
/* This targets elements that are BOTH <p> AND have class "special" */
p.special {
    color: blue;
}

/* This targets elements that are BOTH <div> AND have class "box" AND have class "highlight" */
div.box.highlight {
    background-color: yellow;
}
```

Example usage:
```html
<p>Regular paragraph (not styled)</p>
<p class="special">This paragraph IS blue</p>
<div class="special">This div is NOT blue (not a paragraph)</div>
```


#### Pseudo-class Selectors for Links

Pseudo-classes allow you to style elements based on their state or position. For links (`<a>` elements), there are four important pseudo-classes:

```css
/* Unvisited links */
a:link {
    color: blue;
}

/* Visited links */
a:visited {
    color: purple;
}

/* Mouse over link */
a:hover {
    color: red;
    text-decoration: underline;
}

/* Selected/clicked link */
a:active {
    color: orange;
}
```

Example usage:
```html
<a href="https://example.com">Hover over me!</a>
```

Other common pseudo-classes:
```css
/* First child element */
li:first-child {
    font-weight: bold;
}

/* Last child element */
li:last-child {
    border-bottom: none;
}

/* When an input is focused */
input:focus {
    border-color: blue;
}
```

#### Structural Pseudo-class Selectors

Structural pseudo-classes allow you to select elements based on their position in the document structure. These selectors make it easy to target specific elements within a group of similar elements.

Common structural pseudo-classes:

![Structural Pseudo-class Selectors](https://i.imgur.com/8V2CSTI.png)

```css
/* First element of its type */
li:first-child {
    background: red;
}

/* Last element of its type */
li:last-child {
    background: green;
}

/* Specific element by number (starts at 1) */
p:nth-child(1) {
    background: yellow;
}

/* Every nth element of its type */
p:nth-of-type(2) {
    background: blue;
}
```

Example usage:
```html
<div>
    <p>First p - yellow background</p>
    <p>Second p - blue background</p>
    <p>Third p - no special styling</p>
    
    <ul>
        <li>First li - red background</li>
        <li>Second li - no special styling</li>
        <li>Last li - green background</li>
    </ul>
</div>
```

> 💡 **Pro Tip**: These selectors are particularly useful when you need to style elements based on their position without adding extra classes or IDs!

### CSS Font and Text Properties

Now we are talking about the font and text properties. 

#### Font Properties

1. **font-family**
   - Defines the typeface for text
   - Common values:
     - `serif` (e.g., Times New Roman)
     - `sans-serif` (e.g., Arial)
     - `monospace` (e.g., Courier)
```css
p {
    font-family: Arial, sans-serif;  /* Fallback system */
}
```


2. **font-style**
   - Controls italic or oblique appearance
   - Values:
     - `normal`
     - `italic`
     - `oblique`


3. **font-weight**
   - Controls text thickness
   - Values:
     - `lighter`
     - `normal`
     - `bold`
     - `bolder` (limited font support)

4. **font-size**
   - Sets text size
   - Can use different units (px, em, rem, %)
```css
h1 {
    font-size: 24px;
}
```


#### Text Properties

1. **Text Alignment**
```css
.text {
    text-align: center;    /* left, right, justify */
    vertical-align: middle; /* top, bottom, baseline */
}
```

2. **Text Decoration**
```css
.link {
    text-decoration: underline;           /* line type */
    text-decoration-color: red;           /* line color */
    text-decoration-style: dotted;        /* line style */
    text-decoration-thickness: 2px;       /* line thickness */
}
```

3. **Text Transformation and Spacing**
```css
.text {
    text-transform: uppercase;     /* capitalize, lowercase */
    letter-spacing: 2px;          /* space between characters */
    word-spacing: 4px;           /* space between words */
    line-height: 1.5;           /* line spacing */
}
```

4. **Text Layout**

```css
.paragraph {
    text-indent: 20px;          /* first line indentation */
    white-space: nowrap;        /* text wrapping control */
    text-shadow: 2px 2px 4px #000000; /* shadow effects */
}
```

> 💡 **Pro Tip**: When setting font-family, always include a fallback font system (serif, sans-serif, or monospace) in case the primary font isn't available.





---




### Display Properties: Understanding Block, Inline, and Inline-Block 📦

Think of HTML elements like different types of boxes in a room. Let's see how they behave!

#### 1. Block Elements (`display: block;`) 📦
```css
div {
    display: block;
    width: 200px;
    height: 100px;
    background: #e0e0e0;
}
```
Features:
- Takes up the full width available (like a box that stretches wall-to-wall)
- Always starts on a new line
- Can set width and height
- Common examples: `<div>`, `<p>`, `<h1>`, `<section>`

#### 2. Inline Elements (`display: inline;`) 📝
```css
span {
    display: inline;
    /* width and height won't work! */
    background: yellow;
}
```
Features:
- Flows like text (like words in a sentence)
- Only takes up as much space as needed
- Cannot set width and height
- Common examples: `<span>`, `<a>`, `<strong>`, `<em>`

#### 3. Inline-Block Elements (`display: inline-block;`) 🎁
```css
.inline-block {
    display: inline-block;
    width: 100px;
    height: 100px;
    background: lightblue;
}
```
Features:
- Best of both worlds!
- Flows like inline elements (side by side)
- Can set width and height like block elements
- Perfect for navigation menus or button groups

#### Visual Example:
```html
<div class="block">I'm a block</div>
<span class="inline">I'm inline</span>
<span class="inline">Me too!</span>
<div class="inline-block">Inline-block 1</div>
<div class="inline-block">Inline-block 2</div>
```


> 💡 **Pro Tip**: Think of:
> - Block elements as "paragraphs"
> - Inline elements as "words in a sentence"
> - Inline-block elements as "photos in a text"

#### Common Use Cases:
- Use `block` for structural elements (sections, paragraphs)
- Use `inline` for text-level elements
- Use `inline-block` for navigation items, buttons in a row, or image galleries


| Display Type | Element Flow | Height/Width | Width Behavior | Content | Margin/Padding |
|-------------|--------------|--------------|----------------|---------|----------------|
| **Block** | One element per line | ✅ Can set | Takes 100% of container | Can contain any elements | ✅ All directions work |
| **Inline** | Multiple elements per line | ❌ Cannot set directly | Width of content only | Text or other inline elements | ➡️ Only left/right work |
| **Inline-block** | Multiple elements per line | ✅ Can set | Width of content + set width | Can contain any elements | ✅ All directions work |



----

### CSS Background Properties: Making Beautiful Backgrounds 🎨

Think of backgrounds as the canvas for your web elements. Let's explore how to make them interesting!

#### 1. Background Color
```css
.box {
    /* You can use: */
    background-color: red;                /* Named colors */
    background-color: #ff0000;            /* Hex codes */
    background-color: rgb(255, 0, 0);     /* RGB values */
    background-color: rgba(255, 0, 0, 0.5); /* RGB with opacity */
}
```

#### 2. Background Image 🖼️
```css
.hero {
    background-image: url('path/to/image.jpg');
    /* Pro tip: Always provide a fallback color! */
    background-color: #f0f0f0;
}
```

#### 3. Background Repeat 🔁
```css
.pattern {
    background-image: url('pattern.png');
    background-repeat: repeat;      /* Tile in all directions (default) */
    background-repeat: repeat-x;    /* Repeat horizontally only */
    background-repeat: repeat-y;    /* Repeat vertically only */
    background-repeat: no-repeat;   /* Show image once only */
}
```

#### 4. Background Position 📍
```css
.banner {
    background-position: center;     /* Center the image */
    background-position: top right;  /* Position at top-right corner */
    background-position: 50% 25%;    /* Using percentages */
    background-position: 20px 50px;  /* Using pixel values */
}
```

#### 5. Shorthand Property (All-in-One!) ✨
```css
.hero {
    /* Order: color image repeat position */
    background: #f0f0f0 url('image.jpg') no-repeat center top;
}
```

#### Common Use Cases 🎯

1. **Hero Sections**
```css
.hero {
    background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)),
                url('hero.jpg') no-repeat center/cover;
    height: 100vh;
}
```

2. **Pattern Backgrounds**
```css
.subtle-pattern {
    background: #ffffff url('pattern.png') repeat;
    opacity: 0.2;
}
```

3. **Responsive Backgrounds**
```css
.responsive-bg {
    background-size: cover;  /* Cover entire container */
    background-position: center;
    min-height: 300px;
}
```

> 💡 **Pro Tips:**
> - Always provide a background-color as fallback
> - Use `background-size: cover` for full-width images
> - Consider loading time when using large images
> - Use CSS gradients for better performance when possible







### The Three Core Concepts of CSS: Cascading, Inheritance, and Specificity 🎯

#### 1. Cascading Nature of CSS 

CSS stands for Cascading Style Sheets - but what does "cascading" mean? It's like water flowing down, with styles "cascading" from top to bottom.

```css
/* Later rules override earlier ones */
p {
    color: blue;
}
p {
    color: red;  /* This wins! */
}
```

#### 2. CSS Inheritance 👨‍👧‍👦 - The Family Tree of Styles

Some CSS properties are passed down from parent to child elements, just like genetic inheritance!

```html
<div class="parent">
    I'm the parent text
    <p class="child">
        I'm the child text
        <span class="grandchild">I'm the grandchild text</span>
    </p>
</div>
```

```css
.parent {
    /* These styles will be passed down ✨ */
    color: navy;
    font-family: 'Arial';
    font-size: 16px;
    
    /* These styles stay with the parent 🚫 */
    border: 2px solid red;
    padding: 20px;
    width: 300px;
}
```

What gets Inherited?

Think of it this way:
- **Text-related properties** are like family traits (they pass down)
  - `color` (eye color in the family)
  - `font-family` (the family's accent)
  - `font-size` (height genes)
  - `line-height` (how tall we stand)
  - `text-align` (family's writing style)

- **Box-related properties** are like personal belongings (they don't pass down)
  - `border` (your personal jewelry)
  - `margin` (personal space)
  - `padding` (your clothes)
  - `width/height` (your size)



Common inherited properties:
- `color`
- `font-family`
- `font-size`
- `line-height`
- `text-align`

#### 3. Specificity (Priority Rules) 🏆

Imagine CSS specificity as a fighting tournament where different selectors compete for styling supremacy! Here's how the power levels stack up:


The Championship Ranks 🥇

1. **The Ultimate Power Move: `!important`** ⚡
   ```css
   .regular-button {
       background: red !important;  /* Nuclear option - use with extreme caution! */
   }
   ```
   Like using a cheat code - it wins, but might break the game!

2. **Inline Styles: The Heavy Weight Champion** 🥊
   ```html
   <button style="background: blue;">Click me!</button>
   ```
   Direct but messy - like winning by brute force

3. **ID Selectors: The Professional Fighter** 🎯
   ```css
   #submit-button {
       background: green;
   }
   ```
   Very powerful, but should be used sparingly

4. **Class, Attribute & Pseudo-class: The Skilled Fighters** 💪
   ```css
   .btn-primary { background: yellow; }
   [type="submit"] { background: orange; }
   .nav-link:hover { background: purple; }
   ```
   Your reliable, everyday champions

5. **Element & Pseudo-element: The Amateur Fighters** 🥋
   ```css
   button { background: gray; }
   p::first-line { color: blue; }
   ```
   Good basics, but easily overpowered

6. **Universal Selector: The Rookie** ⭐
   ```css
   * { margin: 0; }
   ```
   Affects everyone but has the least power

#### Real-World Battle Example 🥊
```css
/* Battle for the button color! */

* { background: black; }                /* Power: 0-0-0 */
button { background: blue; }            /* Power: 0-0-1 */
.btn { background: green; }             /* Power: 0-1-0 */
#submit { background: red; }            /* Power: 1-0-0 */
<button style="background: purple;">    /* Inline wins! */

/* The Ultimate Winner */
.btn { background: yellow !important; } /* !important wins all! */
```

> 💡 **Pro Tips for Fair Fighting:**
> - Avoid `!important` unless fighting browser styles or third-party CSS
> - Use classes for most styling needs
> - Keep specificity as low as possible for maintainability
> - Think of IDs as special moves - use them rarely





---

### The CSS Box Model: Building Blocks of Web Layout 📦

Every HTML element is like a box with layers - think of it as a package with wrapping, padding, and contents!

#### The Box Model Layers (from inside out) 🎁


```css
.box {
    /* The actual content */
    width: 200px;
    height: 100px;
    
    /* Padding: Space between content and border */
    padding: 20px;
    
    /* Border: The wrapping around the padding */
    border: 2px solid black;
    
    /* Margin: Space between this box and other elements */
    margin: 30px;
}
```


1. **content-box** (Traditional)
```css
.old-school {
    box-sizing: content-box;
    width: 100px;
    padding: 10px;
    border: 5px solid black;
    /* Total width = 100 + (10 × 2) + (5 × 2) = 130px */
}
```

2. **border-box** (Modern)
```css
.modern {
    box-sizing: border-box;
    width: 100px;
    padding: 10px;
    border: 5px solid black;
    /* Total width = exactly 100px */
}
```




<img src="https://i.imgur.com/jMqoQvy.png" style="zoom:50%;" />

The blue one is the content, the green one is the padding, the red one is the border, and the transparent one is the margin.

#### Padding
padding refers to the space between the content and the border. (内边距) Think of padding like a clock - it starts at the top and goes clockwise:

```css
/* Full version (clockwise from top) */
.box {
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 30px;
    padding-left: 40px;
}

/* Same thing using shorthand! */
.box {
    padding: 10px 20px 30px 40px;
    /*     👆   👆   👆   👆
           top  right bottom left */
}
```

#### Shorthand Magic: Different Ways to Write It ✨

```css
/* 1. All sides the same */
.box {
    padding: 10px;  /* All sides get 10px */
}

/* 2. Vertical | Horizontal */
.box {
    padding: 10px 20px;
    /*     👆   👆
         top/bottom left/right */
}

/* 3. Top | Horizontal | Bottom */
.box {
    padding: 10px 20px 30px;
    /*     👆   👆   👆
          top  sides bottom */
}

/* 4. The full clock */
.box {
    padding: 10px 20px 30px 40px;
    /*     👆   👆   👆   👆
          top right bottom left */
}
```


#### border

border refers to the border of the box. (边框)

Each border has three main properties:
```css
.box {
    border-width: 1px;      /* How thick? */
    border-style: solid;    /* What style? */
    border-color: black;    /* What color? */
}
```

##### Shorthand: The All-in-One Solution ✨
```css
.box {
    /* width | style | color */
    border: 1px solid black;
}
```

##### Border Styles Gallery 🖼️
```css
.border-samples {
    border: 2px solid red;      /* Solid line */
    border: 2px dashed blue;    /* Dashed line ---- */
    border: 2px dotted green;   /* Dotted line .... */
    border: 2px double purple;  /* Double line ═══ */
    border: 2px groove gray;    /* 3D groove effect */
    border: 2px ridge gold;     /* 3D ridge effect */
    border: 2px inset silver;   /* 3D inset effect */
    border: 2px outset bronze;  /* 3D outset effect */
}
```

##### Individual Side Control 🎮
```css
/* Style specific sides */
.box {
    border-top: 1px solid red;
    border-right: 2px dashed blue;
    border-bottom: 3px dotted green;
    border-left: 4px double purple;
}

/* Or be even more specific */
.box {
    border-top-width: 1px;
    border-top-style: solid;
    border-top-color: red;
}
```

#### Margin

margin refers to the space between the box and other elements. (外边距)

. **Using Specific Measurements**
```css
.box {
    /* Using different units */
    margin-top: 20px;     /* Pixels - most common */
    margin-right: 2rem;   /* Relative to root font size */
    margin-bottom: 2em;   /* Relative to element's font size */
    margin-left: 5%;      /* Percentage of parent's width */
}
```

2. **Auto Margins: Browser's Smart Spacing** 🎯
```css
/* Center horizontally */
.center-me {
    margin: 0 auto;    /* Magic centering! */
    width: 80%;        /* Must have a width */
}

/* Let browser decide one side */
.smart-space {
    margin-left: auto;  /* Push element to the right */
}
```

3. **Percentage Margins: Responsive Spacing** 📱
```css
.responsive-element {
    /* Margins relative to parent's WIDTH */
    margin: 5% 10%;    /* Vertical 5%, Horizontal 10% */
}
```

4. **Inherited Margins: Family Values** 👨‍👧‍👦
```css
.child {
    /* Take margin from parent */
    margin: inherit;
}
```

##### Centering Elements & Common Margin Challenges 🎯

**Using Margin Auto** 📏
```css
.center-with-margin {
    width: 300px;  /* Must have a width! */
    margin: 0 auto;  /* Horizontal center */
}
```

2. **Modern Way: Flexbox** 💪
```css
.parent {
    display: flex;
    justify-content: center;     /* Horizontal center */
    align-items: center;         /* Vertical center */
}

/* Or for self-centering */
.child {
    margin: auto;  /* Centers in flex container */
}
```

---



### CSS flexbox

Reference Document:

[Flexbox Playground](https://codepen.io/enxaneta/full/adLPwv/)
[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)

#### What is flexbox?

Flexbox is a layout model that allows you to align and distribute space among items in a container. It's a one-dimensional layout model that can handle both horizontal and vertical layouts.



##### How to use flexbox?

Step 1: Create Your Flex Container

```html
<div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
</div>
```

```css
/* Turn on Flexbox! */
.container {
    display: flex;  /* Magic starts here! ✨ */
    
    /* Optional: Add some style to see the container */
    border: 2px dashed blue;
    padding: 20px;
}

/* Style the items to make them visible */
.item {
    padding: 20px;
    margin: 10px;
    background: #e0e0e0;
    border: 1px solid #999;
}
```

Before Flex vs After Flex

```
┌─────────────────────┐
│ ┌─────┐             │
│ │  1  │             │
│ └─────┘             │
│ ┌─────┐             │
│ │  2  │             │
│ └─────┘             │
│ ┌─────┐             │
│ │  3  │             │
│ └─────┘             │
└─────────────────────┘
```

After (`display: flex`):
```
┌──────────────────────┐
│ ┌─────┐┌─────┐┌─────┐│
│ │  1  ││  2  ││  3  ││
│ └─────┘└─────┘└─────┘│
└──────────────────────┘
```

> 💡 **What Happens When You Add `display: flex`:**
> - Items line up horizontally (by default)
> - Container becomes flexible
> - Items become flex items automatically
> - Ready for further flex properties!



#### Flexbox - two axes : Main and Cross


Think of it like a coordinate system for your layout!


```css
.container {
    display: flex;
    /* By default:
       Main Axis: → (horizontal)
       Cross Axis: ↓ (vertical) */
}
```

#### Flex Direction: Changing the Flow 🔄

1. **Row (Default)** ⮕
```css
.container {
    display: flex;
    flex-direction: row;
}
```

```
Main Axis becomes horizontal (left to right), Cross Axis becomes vertical (top to bottom)
┌──────────────────────┐
│ ┌───┐ ┌───┐ ┌───┐    │
│ │ 1 │ │ 2 │ │ 3 │    │
│ └───┘ └───┘ └───┘    │
└──────────────────────┘
```

2. **Row Reverse** ⬅
```css
.container {
    display: flex;
    flex-direction: row-reverse;
}
```


```
Main Axis becomes horizontal (right to left), Cross Axis becomes vertical (top to bottom)
┌──────────────────────┐
│   ┌───┐ ┌───┐ ┌───┐  │
│   │ 3 │ │ 2 │ │ 1 │  │
│   └───┘ └───┘ └───┘  │
└──────────────────────┘
```


3. **Column** ⬇
```css
.container {
    display: flex;
    flex-direction: column;
}
```

```
Main Axis becomes vertical (top to bottom), Cross Axis becomes horizontal (left to right)
┌──────────────────────┐
│ ┌───┐                │
│ │ 1 │                │
│ └───┘                │
│ ┌───┐                │
│ │ 2 │                │
│ └───┘                │
│ ┌───┐                │
│ │ 3 │                │
│ └───┘                │
└──────────────────────┘
```

4. **Column Reverse** ⬆
```css
.container {
    display: flex;
    flex-direction: column-reverse;
}
```

```
Main Axis becomes vertical (bottom to top), Cross Axis becomes horizontal (left to right)
┌──────────────────────┐
│   ┌───┐              │
│   │ 3 │              │
│   └───┘              │
│   ┌───┐              │
│   │ 2 │              │
│   └───┘              │
│   ┌───┐              │
│   │ 1 │              │
│   └───┘              │
└──────────────────────┘
```

> 💡 **Remember:**
> - Main Axis: Direction items flow (→ ← ↓ ↑)
> - Cross Axis: Always perpendicular to main axis
> - `justify-content`: Controls main axis alignment
> - `align-items`: Controls cross axis alignment



#### Justify-Content: Arranging Items Along the Main Axis

Think of `justify-content` as arranging items on a shelf! Here's how each value works:

##### 1. Basic Alignment
```css
.container {
    display: flex;
    /* Choose your alignment */
    justify-content: flex-start;    /* Default */
    justify-content: center;        /* Center items */
    justify-content: flex-end;      /* Move to end */
}
```

##### Visual Guide to Each Value


1. **flex-start (Default)** 
Items start from beginning
```
┌────────────────────┐
│ [1][2][3]          │
└────────────────────┘

```

2. **center** ⬅

Items centered in container
```
┌────────────────────┐
│    [1][2][3]       │
└────────────────────┘

```

3. **flex-end** 
Items aligned to end
```
┌────────────────────┐
│         [1][2][3]  │
└────────────────────┘

```


4. **space-between** 
Maximum space between items
```
┌────────────────────┐
│ [1]    [2]    [3]  │
└────────────────────┘

```



5. **space-around** 
Equal space around items 
```
┌────────────────────┐
│  [1]  [2]  [3]     │
└────────────────────┘

```

6. **space-evenly** 
Equal space between items
```
┌────────────────────┐
│  [1]  [2]  [3]     │
└────────────────────┘

```


#### Align-Items: Cross Axis Alignment Magic 

1. **stretch (Default)** 

Items stretch to fill container height

<img src="https://i.imgur.com/04HMmkS.png" style="zoom:67%;" />

2. **flex-start** 

<img src="https://i.imgur.com/Ar19efb.png" alt="5" style="zoom:67%;" />

3. **flex-end** 

<img src="https://i.imgur.com/cawMq2j.png" alt="5" style="zoom:67%;" />

4. **center** 

<img src="https://i.imgur.com/ltV9Pkk.png" alt="5" style="zoom:67%;" />

5. **baseline** 

<img src="https://i.imgur.com/FuAyR9r.png" alt="5" style="zoom:67%;" />

### Understanding Flex Item Growth and Shrink 📏

#### Flex Growth and Shrinking Properties

1. **flex-grow: Growing Into Extra Space** 
```html

<div class="container">
    <div class="item">Item 1</div>
    <div class="item item-2">Item 2</div>
    <div class="item">Item 3</div>
</div>
```



```css
.container {
    display: flex;
    width: 500px;
}

/* All items share extra space equally */
.item {
    flex-grow: 1;  /* Each item gets 1 part of extra space */
}

/* Second item gets more space */
.item-2 {
    flex-grow: 2;  /* Gets 2 parts of extra space */
}
```

Visual Example:
```
Default (flex-grow: 0)
┌────────────────────────┐
│ [100px][100px][100px]  │
└────────────────────────┘

With flex-grow: 1
┌────────────────────────┐
│ [====][====][====]     │
└────────────────────────┘

Mixed flex-grow (1,2,1)
┌────────────────────────┐
│ [===][======][===]     │
└────────────────────────┘
```

2. **flex-shrink: Handling Small Spaces** 📉
```css
.item {
    flex-shrink: 1;  /* Default - will shrink if needed */
}

.keep-size {
    flex-shrink: 0;  /* Won't shrink */
}
```

3. **flex-basis: Starting Size** 📏
```css
.item {
    flex-basis: 200px;  /* Starting width (in row direction) */
    flex-basis: auto;   /* Use item's content width */
}
```

#### Shorthand Property ✨
```css
.item {
    /* flex: grow shrink basis */
    flex: 1 1 auto;    /* Can grow and shrink, auto basis */
    
    /* Common patterns */
    flex: 1;           /* Can grow, can shrink, 0 basis */
    flex: auto;        /* Can grow, can shrink, auto basis */
    flex: none;        /* Can't grow, can't shrink, auto basis */
}
```

#### Real World Examples 🌟

1. **Navigation Bar**
```css
.nav {
    display: flex;
}
.logo {
    flex-shrink: 0;     /* Logo
```



---


[^1]: A programming language needs to have constructs like variables (traditional CSS), loops, or functions, and it can perform computations or make decisions

