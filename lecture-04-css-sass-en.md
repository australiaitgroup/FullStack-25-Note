## Lecture04 CSS & Sass

> This note is based on the lecture ([link](https://jiangren.com.au/study/lesson?programId=672448ecea33cf003687af93&lessonId=673c41cb0022bb00124fe2ed&tab=content) by Ally Tang. The entire lecture is about CSS (**Cascading Style Sheets**). If doubts, please ask anyone or consult the documentation [W3School](https://www.w3schools.com/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML). Happy Coding



## Table of Contents

- [CSS - Cascading Style Sheets](#css---cascading-style-sheets)
  - [CSS Units](#css-units)
  - [CSS Naming Methodologies](#css-naming-methodologies)
    - [BEM Block Element Modifier](#bem-block-element-modifier)
    - [Traditional CSS VS BEM CSS](#traditional-css-vs-bem-css)
    - [BEM Naming Convention](#bem-naming-convention)
    - [BEM Naming Rules](#bem-naming-rules)
  - [Responsive Design Using Media Queries](#responsive-design-using-media-queries)
    - [Basic Media Query Syntax](#basic-media-query-syntax)
    - [Common Breakpoints Example](#common-breakpoints-example)
    - [Key Concepts](#key-concepts)
      - [Mobile-First vs Desktop-First](#mobile-first-vs-desktop-first)
      - [Common Breakpoints](#common-breakpoints)
      - [Important Rules](#important-rules)
    - [Interactive Example: Responsive Card Layout](#interactive-example-responsive-card-layout)
  - [Position](#position)
    - [Position Examples](#position-examples)
      - [Example 1: Relative vs Absolute Positioning](#example-1-relative-vs-absolute-positioning)
      - [Example 2: Sticky Navigation](#example-2-sticky-navigation)
      - [Example 3: Fixed Modal Overlay](#example-3-fixed-modal-overlay)
  - [Transition](#transition)
    - [Example 1: Transition on Hover](#example-1-transition-on-hover)
    - [Example 2: Transition on Click](#example-2-transition-on-click)
  - [Z-index](#z-index)
    - [Basic Example](#basic-example)
    - [Stacking Context Example](#stacking-context-example)
    - [Modal Overlay Example](#modal-overlay-example)
    - [Key Points About z-index](#key-points-about-z-index)
  - [Grid](#grid)
    - [Flex One-dimensional](#flex-one-dimensional)
    - [Grid Two-dimensional](#grid-two-dimensional)
    - [Grid vs Flexbox Comparison](#grid-vs-flexbox-comparison)
    - [Real-World Usage Pattern](#real-world-usage-pattern)
    - [Why Grid is Powerful Yet Flexbox is Used More Often](#why-grid-is-powerful-yet-flexbox-is-used-more-often)

- [Sass](#sass)
  - [Sass Introduction](#sass-introduction)
    - [What a CSS preprocessor is](#what-a-css-preprocessor-is)
    - [What is Sass](#what-is-sass)
    - [Difference between Sass and Scss](#difference-between-sass-and-scss)
    - [How does Sass actually work](#how-does-sass-actually-work)
    - [Why should you use Sass](#why-should-you-use-sass)
  - [Feature of Sass](#feature-of-sass)
    - [Variables in Sass](#variables-in-sass)
    - [Nesting in Sass](#nesting-in-sass)
    - [Parent Selector](#parent-selector)
    - [Mixin and Include](#mixin-and-include)
    - [Import and Partials](#import-and-partials)
    - [Extend and Inheritance](#extend-and-inheritance)
    - [How to use Conditional statement in SCSS](#how-to-use-conditional-statement-in-scss)
    - [Function and operators](#function-and-operators)
  - [How to Set Up Sass for Local Development](#how-to-set-up-sass-for-local-development)
    - [VS Code](#vs-code)
    - [For Mac OS X or Linux](#for-mac-os-x-or-linux)
  - [Tips for using Sass](#tips-for-using-sass)




---



##  1. Cascading Style Sheets (CSS)

### 1.1. CSS Units

##### Absolute Length Units
| Unit | Full Form | Example Usage | Common Uses |
|------|-----------|---------------|-------------|
| `px` | Pixel | `font-size: 16px` | Small precise measurements like borders; specific positioning |
| `pt` | Point | `font-size: 12pt` | Traditional print measurements |
| `pc` | Pica | `font-size: 1pc` | Traditional print measurements |
| `in` | Inches | `font-size: 1in` | Print-specific layouts |
| `cm` | Centimeter | `font-size: 1cm` | Print-specific layouts |
| `mm` | Millimeter | `font-size: 10mm` | Print-specific layouts |
| `q` | Quarter | `font-size: 16q` | Very small measurements (1q = 1/4mm) |



###### **Absolute Length Units:**
- Fixed measurements that remain constant regardless of device or parent element
- Best used for:
  - Print layouts where physical measurements matter
  - When the output size needs to be precisely controlled
  - Elements that should maintain exact dimensions

- Example:

```css
.business-card {
    width: 3.5in;    /* Standard business card width */
    height: 2in;     /* Standard business card height */
}

.border-thin {
    border: 1px solid black;  /* Precise border width */
}
```
- Codepen sandbox - [link](https://codepen.io/shenghongzhong/pen/JoPOmgG)

<iframe height="500" style="width: 100%;" scrolling="no" title="Example-absolute units" src="https://codepen.io/shenghongzhong/embed/JoPOmgG?default-tab=result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/JoPOmgG">
  Example-absolute units</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>


##### Relative Length Units
| Unit | Description | Relative To | Common Uses |
|------|-------------|-------------|-------------|
| `em` | Element-relative | Current element's font-size | Element dimensions (width, height, padding, margin) |
| `rem` | Root-relative | Root element's font-size | Font sizes and spacing; maintains consistency |
| `ex` | x-height | Font's x-height | Typography-specific measurements |
| `ch` | Character | Width of "0" digit | Typography and monospace layouts |
| `%` | Percentage | Parent element | Responsive layouts and sizing |
| `vw` | Viewport width | 1% of viewport width | Responsive full-width layouts |
| `vh` | Viewport height | 1% of viewport height | Responsive full-height layouts |
| `vmin` | Viewport minimum | Smaller of vw or vh | Responsive design for varying viewports |
| `vmax` | Viewport maximum | Larger of vw or vh | Responsive design for varying viewports |

###### **Relative Length Units:**

- Measurements that scale based on another element or viewport
- Best used for:
  - Responsive web design
  - Maintaining proportions across different screen sizes
  - Accessibility (allowing text to scale with user preferences)

- Example:
```css
.container {
    width: 80%;          /* Relative to parent width */
    max-width: 1200px;   /* Maximum width constraint */
}

.hero-section {
    height: 100vh;       /* Full viewport height */
    padding: 2rem;       /* Relative to root font size */
}

.text-content {
    font-size: 1.2em;    /* 20% larger than parent font size */
    line-height: 1.5;    /* 1.5 times the element's font size */
}
```

Codepen Sandbox - [link](https://codepen.io/alice-tang/pen/vYpJxqy)


<iframe 
    height="600" 
    style="width: 100%;" 
    scrolling="no" 
    title="Example-relative-units" 
    src="https://codepen.io/shenghongzhong/embed/JoPOejX?default-tab=css%2Cresult" 
    frameborder="no" 
    loading="lazy" 
    allowtransparency="true" 
    allowfullscreen="true">
</iframe>


**When to Use Which:**
- Use absolute units (`px`, `pt`, etc.) for:
  - Print stylesheets
  - Border widths
  - Fixed-size elements that shouldn't scale
- Use relative units (`rem`, `em`, `%`, etc.) for:
  - Font sizes
  - Padding and margins
  - Responsive layouts
  - Container widths
  - Any element that should scale with screen size or user preferences




### 1.2 CSS Naming Methodologies

##### BEM-Block Element Modifier

**What is BEM?**
BEM is a popular CSS naming methodology developed by Yandex in 2009. It provides a modular approach to web development by breaking down interfaces into reusable components. The name BEM stands for Block, Element, Modifier – the three core entities that form the foundation of this methodology.

**Why BEM Became Popular:**

1. **Maintainability**
   - Makes CSS more maintainable and scalable for large projects
   - Reduces specificity conflicts
   - Makes code easier to understand for new team members

2. **Reusability**
   - Creates modular components that can be reused across projects
   - Reduces CSS code duplication
   - Makes it easier to update and modify components

3. **Structure**
   - Provides clear and strict naming rules
   - Makes relationships between HTML and CSS more visible
   - Helps developers understand component hierarchy at a glance

##### **Traditional CSS V.S. BEM CSS**

###### Traditional CSS

Codepen Sandbox - [link](https://codepen.io/shenghongzhong/pen/RNbjqKx)

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/shenghongzhong/embed/RNbjqKx?default-tab=result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/RNbjqKx">
  Untitled</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
###### BEM CSS

Codepen Sandbox - [link](https://codepen.io/shenghongzhong/pen/ogvoQZW)

<iframe height="300" style="width: 100%;" scrolling="no" title="Example-with-BEM" src="https://codepen.io/shenghongzhong/embed/ogvoQZW?default-tab=result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/ogvoQZW">
  Example-with-BEM</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
##### **BEM Naming Convention**

- Block: Standalone component that is meaningful on its own (e.g., `header`, `menu`, `button`)
- Element: Parts of a block that have no standalone meaning (`__`) (e.g., `menu__item`, `header__title`)
- Modifier: Flags on blocks or elements that change appearance or behavior (`--`) (e.g., `button--large`, `menu__item--active`)

Example
```css
/* Block component */
.card { }

/* Element that depends upon the block */ 
.card__title { }
.card__image { }

/* Modifier that changes the style of the block */
.card--featured { }
.card__title--large { }
```

##### **BEM Naming Rules:**

- `-` Hyphen: Used for word separation in long names (e.g., `block-name`)
- `__` Double underscore: Connects element to block (e.g., `block__element`)
- `--` Double hyphen: Indicates modifier (e.g., `block--modifier`)





### 1.3 Responsive Design Using Media Queries

Media queries are a fundamental CSS feature that allows us to create responsive layouts by applying different styles based on device characteristics like screen width. This enables us to adapt our designs for mobile, tablet, and desktop devices.

#### Basic Media Query Syntax
```css
/* Basic structure */
@media screen and (max-width: 768px) {
    /* Styles here */
}
```

#### Common Breakpoints Example
```css
/* Default styles (Desktop first approach) */
.container {
    width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* Tablet styles */
@media screen and (max-width: 1024px) {
    .container {
        width: 90%;
    }
}

/* Mobile styles */
@media screen and (max-width: 768px) {
    .container {
        width: 95%;
        padding: 10px;
    }
}
```

#### Common Media Types:
- `screen`: For computer screens, tablets, and phones
- `all`: For all devices
- `print`: For printers and print preview
- `speech`: For screen readers

#### Key Concepts
##### 1. **Mobile-First vs Desktop-First**

```css
/* Mobile-First approach using min-width */
.element { 
    /* Mobile styles by default */
    width: 100%;
}

@media (min-width: 768px) {
    /* Tablet styles */
    .element {
        width: 50%;
    }
}

@media (min-width: 1024px) {
    /* Desktop styles */
    .element {
        width: 33.33%;
    }
}
```

##### 2. **Common Breakpoints**

- Mobile: < 768px
- Tablet: 768px - 1024px
- Desktop: > 1024px

##### 3. **Important Rules**

- Order matters: Place media queries in order from most general to most specific
- Avoid overlapping ranges to prevent style conflicts
- Test across different devices and orientations


#### Interactive Example-Responsive Card Layout

Here's a practical example you can try in your browser that demonstrates both mobile-first and responsive design principles:

##### **Traditional CSS**

Codepen sandbox - [link](https://codepen.io/shenghongzhong/pen/emOeQRN)

<iframe height="600" style="width: 100%;" scrolling="no" title="Example-Responsive-Design-without-BEM" src="https://codepen.io/shenghongzhong/embed/emOeQRN?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/emOeQRN">
  Example-Responsive-Design-without-BEM</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

##### BEM CSS

Codepen Sandbox [link](https://codepen.io/shenghongzhong/pen/MYgOzvW)

<iframe height="600" style="width: 100%;" scrolling="no" title="Example-Rsponsive-Design-BEM" src="https://codepen.io/shenghongzhong/embed/MYgOzvW?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/MYgOzvW">
  Example-Rsponsive-Design-BEM</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

### 1.4 Position

The `position` property controls how elements are positioned:

- `static`: Default value. Elements appear in their normal position in the document flow.
- `relative`: Positions the element relative to its normal position in the document flow. Key characteristics:

  1. Positioned relative to its original position
  2. Maintains its original space in the document flow (other elements won't occupy its original position)

  ```css
  div {
    width: 100px;
    height: 100px;
    position: relative; /* Enable relative positioning */
    top: 100px;
    left: 100px;
  }
  /* This example moves the element 100px down and 100px right */
  ```

  Properties for adjusting position relative to the element's original position in the document flow:

  - `top: 100px;` moves down 100px
  - `top: -100px;` moves up 100px
  - `right: 100px;` moves left 100px
  - `right: -100px;` moves right 100px
  - `bottom: 100px;` moves up 100px
  - `bottom: -100px;` moves down 100px
  - `left: 100px;` moves right 100px
  - `left: -100px;` moves left 100px

- `absolute`:
  - Positions relative to the nearest positioned ancestor (any ancestor with position other than static). If no positioned ancestors exist, positions relative to the document root.
  - Removes the element from the normal document flow.
    > Must set at least one of left, top, right, or bottom for absolute positioning to take effect.

- `fixed`: Positions relative to the browser window, removed from the normal document flow. Commonly used for floating elements.

  ```css
  position: fixed;
  top: 0;
  left: 0;
  /* This example fixes the element to the top-left corner of the viewport */
  ```

- `sticky`:

  Elements become "stuck" when they reach a specified position in the viewport.

  ```css
  position: sticky;
  top: 20px;
  /* This example makes the element stick 20px from the top of its container when scrolling */
  ```

  > Must set at least one of top, left, right, or bottom for sticky positioning to work.

  `fixed` _vs._ `sticky`

  > While fixed completely fixes an element's position, sticky only fixes the position after scrolling to a certain point. Their use cases sometimes overlap.



##### Position Examples

###### Example 1- Relative vs Absolute Positioning
This example demonstrates the relationship between relative and absolute positioning:

Codepen sandbox - [link](https://codepen.io/shenghongzhong/pen/YPKERrY)


<iframe height="500" style="width: 100%;" scrolling="no" title="Example-position" src="https://codepen.io/shenghongzhong/embed/YPKERrY?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/YPKERrY">
  Example-position</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>




###### Example 2- Sticky Navigation
A common use case for sticky positioning - a navigation bar that sticks to the top when scrolling:

codepen sandbox - [link](https://codepen.io/shenghongzhong/pen/QwLOJqR)

<iframe height="500" style="width: 100%;" scrolling="no" title="Example-sticky-navigation" src="https://codepen.io/shenghongzhong/embed/QwLOJqR?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/QwLOJqR">
  Example-sticky-navigation</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>



###### Example 3- Fixed Modal Overlay
Demonstrates how to create a modal that stays fixed regardless of scrolling:

Codepen sandbox - [link](https://codepen.io/shenghongzhong/pen/ZYzamaG)

<iframe height="500" style="width: 100%;" scrolling="no" title="Example-Fixed Modal Overlay" src="https://codepen.io/shenghongzhong/embed/ZYzamaG?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/ZYzamaG">
  Example-Fixed Modal Overlay</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>


##### Key Takeaways
1. Use `relative` positioning when you want to adjust an element's position while maintaining its space in the document flow
2. Use `absolute` positioning with a `relative` parent for precise control over element placement
3. Use `sticky` for elements that should stick to a position during scroll
4. Use `fixed` for elements that should stay in place regardless of scrolling

> 💡 **Pro Tip**: When working with positioned elements, remember that `z-index` only works on elements with a position value other than `static`.




### 1.5 Transition

In CSS, transition is a property that allows you to control the smoothness of changes in property values over time. It makes changes in property values appear gradually, rather than abruptly.

<img src="https://i.imgur.com/qiA1Gab.png" style="zoom:50%;" />



Syntax:

```css
selector {
  transition: property duration timing-function delay;
}
```

Example

```css
.box {
  background-color: blue;
  transition: background-color 0.5s ease;
}

.box:hover {
  background-color: red;
}
```

- property: The CSS property you want to animate.
- duration: The time it takes for the animation to complete.
- timing-function: The speed curve of the animation.
- delay: The time before the animation starts.




##### Example 1- Transition on Hover

Codepen box - [link](https://codepen.io/shenghongzhong/pen/yyBPQpL)

<iframe height="300" style="width: 100%;" scrolling="no" title="Example-transition" src="https://codepen.io/shenghongzhong/embed/yyBPQpL?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/yyBPQpL">
  Example-transition</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
Note: Transitions can be triggered not only through pseudo-classes like `:hover`, but also by using JavaScript to add or remove classes, giving you programmatic control over when transitions take effect.



##### Example 2- Transition on Click -Use JavaScript to add or remove classes

Codepen box - [link](https://codepen.io/shenghongzhong/pen/JoPOeMW)

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/shenghongzhong/embed/JoPOeMW?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/JoPOeMW">
  Untitled</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>



### 1.6 z-index

z-index is a CSS property that controls the stacking order of elements. It determines which element should appear above or below other elements when they overlap.

#### Basic Example

Codepen box - [link](https://codepen.io/shenghongzhong/pen/ByBmGJG)

<iframe height="300" style="width: 100%;" scrolling="no" title="example-z-index" src="https://codepen.io/shenghongzhong/embed/ByBmGJG?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/ByBmGJG">
  example-z-index</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>


#### Stacking Context Example

A stacking context is created when certain properties are used. Here's an example showing how z-index behaves within different stacking contexts:

codepen box - [link](https://codepen.io/shenghongzhong/pen/MYgOzQY)

<iframe height="600" style="width: 100%;" scrolling="no" title="example-z-index-stacking-content" src="https://codepen.io/shenghongzhong/embed/MYgOzQY?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/MYgOzQY">
  example-z-index-stacking-content</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
#### 

#### Modal Overlay Example

A practical use case for z-index with a modal overlay:

codepen box - [link](https://codepen.io/shenghongzhong/pen/ogvoQEG)

<iframe height="300" style="width: 100%;" scrolling="no" title="Example-z-index-Modal Overlay" src="https://codepen.io/shenghongzhong/embed/ogvoQEG?default-tab=css%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/shenghongzhong/pen/ogvoQEG">
  Example-z-index-Modal Overlay</a> by Shenghongzhong (<a href="https://codepen.io/shenghongzhong">@shenghongzhong</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>
#### 

#### Key Points About z-index

1. **Only works on positioned elements**: Elements must have a position value other than `static`
2. **Creates stacking context**: Some CSS properties create a new stacking context:
   - Elements with position: fixed or sticky
   - Elements with opacity less than 1
   - Elements with transform, filter, or perspective
3. **Numeric values**: Can be positive or negative integers
   - Higher values appear on top
   - Default value is `auto` (equivalent to 0)
4. **Scope**: z-index only competes with elements within the same stacking context

#### Best Practices:

1. Use meaningful z-index values (avoid arbitrary large numbers)
2. Keep a z-index scale (e.g., 1-10 for normal content, 100s for overlays, 1000s for modals)
3. Document your z-index hierarchy
4. Be aware of stacking contexts to avoid unexpected behavior

> 💡 **Pro Tip**: When dealing with z-index issues, check if your elements are creating new stacking contexts, as this is a common source of confusion.



### 1.7 Grid

css grid is very powerful. In practice, flex is used more than grid

**Flex (One-dimensional)**

\- Works along a single axis (either row OR column) at a time

\- Like items on a line or in a stack

\- Think of it as arranging items in a single row or column

```css
/* Row layout (horizontal) */
.flex-row {
    display: flex;
    flex-direction: row;
}

/* Column layout (vertical) */
.flex-column {
    display: flex;
    flex-direction: column;
}
```



**Grid (Two-dimensional)**

\- Works with rows AND columns simultaneously

\- Like a spreadsheet with cells

\- Think of it as creating a complete layout grid



```css
/* Basic grid layout */
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;  /* 3 equal columns */
    grid-template-rows: auto auto;        /* 2 rows */
}
```





#### Grid vs. Flexbox Comparison

| Feature | CSS Grid | Flexbox |
|---------|----------|---------|
| Dimension | Two-dimensional (rows AND columns) | One-dimensional (rows OR columns) |
| Best Used For | Overall page layout | Component layout |
| Direction | Works from both directions simultaneously | Works in either row OR column |
| Control | Precise control over both dimensions | Control over single dimension |
| Gap Control | Built-in row and column gaps | Only in one direction |
| Alignment | Both dimensions simultaneously | One dimension at a time |

##### When to Use Grid:
- Creating overall page layouts
- Working with both rows and columns simultaneously
- Complex grid-based designs
- When you need precise control over both dimensions
- Magazine-style layouts
- Card layouts with specific row/column requirements

```css
/* Grid Example */
.grid-layout {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: auto;
    gap: 20px;
}
```

##### When to Use Flexbox:
- Component-level layouts
- Navigation bars
- Single row or column layouts
- When content size should dictate layout
- Dynamic content where exact dimensions aren't known
- When you need more flexibility in one dimension

```css
/* Flexbox Example */
.flex-layout {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 20px;
}
```

#### Real-World Usage Pattern
Most modern websites use a combination of both:
```css
/* Page structure with Grid */
.page-layout {
    display: grid;
    grid-template-areas: 
        "header header"
        "sidebar main"
        "footer footer";
    grid-template-columns: 200px 1fr;
}

/* Component layout with Flexbox */
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
```

#### Why Grid is Powerful Yet Flexbox is Used More Often

1. **Learning Curve**
   - Flexbox: Simpler to learn and implement
   - Grid: More complex with more properties to master

2. **Browser Support**
   - Flexbox: Better legacy browser support
   - Grid: Excellent modern browser support but may need fallbacks for older browsers

3. **Use Case Frequency**
   - Flexbox: Handles common UI patterns (navigation, lists, cards)
   - Grid: Better for complex layouts but needed less frequently

4. **Development Speed**
   - Flexbox: Quicker to implement for simple layouts
   - Grid: Requires more planning but provides more control

> 💡 **Pro Tip**: Start with Flexbox for component-level layouts and use Grid when you need precise control over both dimensions or are creating complex page layouts.

- Container and items

  ```html
  <body>
    <div class="wrapper">
      <div class="one item">One</div>
      <div class="two item">Two</div>
      <div class="three item">Three</div>
      <div class="four item">Four</div>
      <div class="five item">Five</div>
      <div class="six item">Six</div>
    </div>
  </body>
  ```

  - To enable grid layout for a container: `display: grid;`

- Rows and columns

  - Container is divided into row (horizontal) and column (vertical)
  - Use `grid-template-columns` and `grid-template-rows` to define row and column widths
    Example

    ```css
    .wrapper {
      display: grid;
      grid-template-columns: 100px 100px 100px;
      grid-template-rows: 100px 100px 100px;
    }
    ```

    - repeat() function is used to repeat grid row or column patterns. It takes two arguments: repeat count and template, e.g., `grid-template-columns: repeat(3, 1fr);`
    - `auto-fill` attribute can be used with repeat() to automatically fill the grid container with grid items, adapting to the container's width. This is useful in responsive design.
    - `fr` attribute is used to specify the proportional distribution of space within the grid container. For example, `grid-template-columns: 1fr 2fr 1fr;`
    - `minmax()` attribute defines the minimum and maximum size of grid items.

    Example

    ```css
    grid-template-columns: repeat(auto-fill, 200px);
    grid-template-columns: 200px 1fr 2fr;
    grid-template-columns: 1fr 1fr minmax(300px, 2fr);
    
    grid-gap: 20px;
    grid-row-gap: 20px;
    grid-column-gap: 20px;
    
    grid-template-rows: 100px 200px; /* row height */
    ```

  - Use `grid-row-gap`, `grid-column-gap`, and `grid-gap` to set gap
  - Understand `justify-items`, `align-items`, `justify-self`, and `align-self` properties, which can be used to control alignment within the grid container and grid items.

Some flex properties can also be used in CSS Grid, such as justify-content







### 

-----

## 2. Sass

### 2.1 Sass Introduction

#### What a CSS preprocessor is?

> A CSS preprocessor is a program that lets you generate CSS from the preprocessor's own unique syntax.



There are other preprocessor languages include less, PostCSS etc. 

<img src="https://i.imgur.com/3dAL8Ed.png" style="zoom:50%;" />



#### What is Sass?

As mentioned above, Sass, stands for **Syntactically Awesome Style Sheet**), is one of CSS preprocessors that enable us to write clean reusable CSS rules.



#### Difference between Sass and Scss

I was confused to see Sass and Scss. After some digging out, I realised the mechanism of Sass and Scss is the same, and **the only difference between them is their syntax.** 



##### Sass

```Sass
nav
  ul
    margin: 0
    padding: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    text-decoration: none
```



##### Scss

```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }

  a {
    display: block;
    text-decoration: none;
  }
}
```





#### How does Sass actually work?

![](https://i.imgur.com/rf1s8ny.png)

As far as I am concerned, Sass or Scss is a file. There is a compiler to convert them to original CSS code so HTML files can be styled by css files. This is because HTML only renders CSS files. 

In summary, Sass works in such a way that when you write your styles in a `.scss` file, it gets compiled into a regular CSS file. The CSS code is then loaded into the browser.





#### Why should you use Sass?



- **DRY (Don't Repeat Yourself)** : It can reduce repetitive CSS code, saving time.

- **Easy to learn**: If you are familiar with CSS already, then you'll be glad to know that Sass actually has a similar syntax, and so you can start using it, even after this tutorial ;)
- **Compatibility**: It is compatible with all versions of CSS. So, you can use any available CSS libraries.
- **Saves time**: It helps reduce the repetition of CSS, because of its powerful features.
- **Reusable code**: It opens up the possibility of modularization. Sass allows for variables and chunks of code (mixins) that can be reused over and over again. This helps you save time and makes you able to code faster.
- **Organised Code**: Sass helps keep your code organized by using partials.
- **Cross Browser Compatibility**: Sass gets compiled into CSS and adds all the necessary vendor prefixes so you don't have to worry about manually writing them out.



HTML cannot deal with Scss or Sass file, therefore you woould only write `.scss` file  during the development phase, and `.scss` files are compiled into CSS files using VS code plugins or packages or other method.

> VS code plugin: **`Live Sass Compoiler`**



### 2.2 Feature of Sass

Sass has 5 features:

1. Variables
2. Nesting
3. Mixin
4. Partials
5. Extent/Inheritance

### Variables in Sass

I was surpirsed to see some features of Sass but also understand why it is necessary after writing some messy CSS code. 

So you can declare variables in Sass file. It is one of good stuff about using Sass to write css code. Because you can use some featues of Sass to import and reuse variables everywhere once you define them. This allows us to build a CSS design system. 



One of benefits for using variables is that if that value changes, you simply need to update a single line of code.



```SCSS
$myFont: Helvetica, sans-serif;
$myColor: red;
$myFontSize: 18px;
$myWidth: 680px;

p {
    color: $myColor;
    font-size: $myFontSize;
}
```

**Scope**: Sass variables are only available within the nesting level where they are defined. This means you can't use it if you define a variable in a one element. See an example as follows:

![](https://i.imgur.com/6EWbP1S.png)



![](https://i.imgur.com/gLgA2Nw.png)



Then you can't use the variable `--stop` for `p` in `.scss`





### Nesting in Sass

I don't know about you but I often felt vomiting while writing CSS as there are often duplicated CSS rules. Therefore, Sass comes in use and lets you nest CSS selectors in the same way as HTML.


 The following CSS code is the valina CSS but we need to rewrite them into Sass.

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav li {
  display: inline-block;
}
nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```

Rewritten Sass code

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
    &hover {
      color: #0695c;
    }
  }
}
```





### Parent Selector - `&`

In the Sass code above, you might notice the ampersand symbol `&` used with the hover pseudo-class. This is called a Parent Selector.

The parent selector, `&`, is a special selector invented by Sass that's used in nested selectors to refer to the outer selector. Source – [Sass Documentation](https://sass-lang.com/documentation/style-rules/parent-selector)



How do you implement Sass with BEM naming practice? 

- [Write Cleaner CSS using BEM](https://israelmitolu.hashnode.dev/writing-cleaner-css-using-bem-methodology)

- [BEM Methodology Docs](https://en.bem.info/methodology/)
- [BEM Cheatsheet](https://9elements.com/bem-cheat-sheet/)
- [BEM for Beginners](https://www.smashingmagazine.com/2018/06/bem-for-beginners/)



### Mixin and Include

Use the directive `@mixin`  to create reusable code (blocks).  
Use the directive `@include`  to use what the reusable code (blocks) is previously created by `@mixin`.

Syntax:

```scss
@mixin customised-mixin-name {
  property: value;
  property: value;
}

div {
  @include customised-mixin-name;
}
```

Example:

```scss
@mixin style($size: 15px, $color: #999) {
  font-size: $size;
  color: $color;
  line-height: 1.5;
}

div {
  @include style(25px, black);
}
```

> The above example demonstrates how parameters can be passed to mixins, allowing for redefined font size and color.



### Import and Partials

Partials help you organise and structure your CSS code. As stylesheets grow large over time, it gets difficult to maintain them.  it just makes sense to break your stylesheets into smaller chunks. 



Partials are files that start with an underscore  `_`. For example, we have a `_globals.scss`, `_variables.scss`, and `_buttons.scss`, `_reset.scss` we could import them into the main SCSS file `main.scss`.

In order to import those pre-defined code, we need to use the directive `@import`  in the `main.scss`

```scss
@import "reset";
@import "globals";
@import "variables";
@import "buttons";
```

Note:

- You'll notice that the underscore `_` and the `.scss` are not added. That is because **Sass automatically assumes that you are referring to the `.sass` or `.scss` file.**

- By default, Sass directly compiles all `.scss` files. However, you may want to import files without compiling them.

- If a file name starts with an underscore, Sass will not compile it. Because `main.scss` will import them which is the main `.scss` file should be compiled





### Extend and Inheritance

Sass has a few ways to help achive this goal of the DRY principle. One of the ways of doing this is to create a placeholder that can be extended with `@extend` . You can use the placeholder variable, the percentage  `%` symbol, to create a selector that you only want to extend. Extending means giving a css class the attributes of the extended class. This way we don’t have to write the same code over and over.

```scss
/* This CSS will print because %message-shared is extended. */
%message-shared
  border: 1px solid #ccc
  padding: 10px
  color: #333


// This CSS won't print because %equal-heights is never extended.
%equal-heights
  display: flex
  flex-wrap: wrap


.message
  @extend %message-shared


.success
  @extend %message-shared
  border-color: green


.error
  @extend %message-shared
  border-color: red


.warning
  @extend %message-shared
  border-color: yellow
```

To extend, as it is shown, all you have to do is use “@extend” with the “%” symbol and class name. This will ensure that the success, error, and warning class all have the attributes from the “message-shared” class.



We need to talk about the inheritance for CSS selector. Inheritance allows a CSS selector to inherit all styles from another selector.  Hence, using `@extend `works .

> Must be used with `%` placeholder selectors

Example:

```scss
/* the code block has the name `button-style` */
%button-style {
  background-color: blue;
  color: white;
  padding: 10px 20px;
}

.button {
  @extend %button-style;
}

.success-button {
  @extend %button-style;
  background-color: green;
}
```

In the above example, `%button-style` is a placeholder selector that defines a button style. Then, `.button` class inherits this style, and `.success-button` inherits the same style but overrides the background color to green.

In the complied CSS, `.button` and `.success-button` will both include the styles from `%button-style`, avoiding duplicate styles.



### How to use Conditional statement in SCSS



```scss
@mixin body-theme($theme) {
  @if $theme == "light" {
    background-color: $light-bg;
  } @else {
    background-color: $dark-bg;
  }
}
```



### Function and operators

Prior to Sass, you couldn’t perform any math in a CSS file. Operators in Sass change this by giving you the ability to do math with your attributes.



```scss
.container {
  width: 100%;
}

article[role="main"] {
  float: left;
  width: 600px / 960px * 100%;
}

aside[role="complementary"] {
  float: right;
  width: 300px / 960px * 100%;
}
```



Sass offers built-in functions that enable us to do calculations and operations that return a specific value.  They range from color calculations to math operations like getting random numbers and calculation of sizes, and even conditionals.

It also provides support for mathematical operators like `+`, `-`, `\`, `*`, `/`, and `%`, which we can use with the `calc` function.



Here is an example using a pixel to rem conversion function:

```scss
@function pxToRem($pxValue) {
  $remValue: ($pxValue / 16) + rem;
  @return $remValue;
}

div {
  width: pxToRem(480);
}
```



Or use the `math` library from Sass.



```scss
@use "sass:math";

@function pxToRem($pxValue) {
  @return math.div($pxValue, 16px) * 1rem;
}

div {
  width: pxToRem(480px); // gives 30rem
}
```

#### Built-in functions

Built-in functions: SCSS has many built-in functions for handling colors, math operations, string manipulation, etc.
Example: In SCSS, `lighten()`,  `darken()` and `round()` are built-in functions 

```scss
$color: darken(#3498db, 10%);
$result: round(5.7);
```

#### User-defined functions

Custom functions: Use  the directive`@function`  to create custom functions. 
Example

```scss
// Define custom function
@function add-margin($value) {
  @return $value + 10px;
}

// Use custom function
.box {
  margin: add-margin(20px);
}

// margin is 30px
```





### 2.3 How to Set Up Sass for Local Development



You have some options to compile Sass files to `.css` files

- VS Code Extension
- Install using NPM globally
- Install using open source apps such as Compass.app, Live Reload, and Koala.
- Install using Homebrew (for MacOS)



#### VS Code

##### Step 1: Install Live Sass Compiler

First, launch Visual Studio Code. Once it's loaded, go to the side panel on the left and select the extensions tab.



![](https://i.imgur.com/nL6JKPR.png)



*Extensions tab in VS Code*



In the search bar, search for "Live Sass Compiler" and install it. This extension helps us to compile the Sass files — `.scss` (or `.sass`) – into `.css` files.





##### Step 2: Set the Save Location

Now change the file path so that Sass gets compiled into the `styles` folder. To do this, you will make changes to the `settings.json` file. In VS Code, go to File > Preferences > Settings. Now search for `live sass compile` to change the global settings.



Click on `Edit settings.json`.



Now, on the first few lines, where you see this code:



```
{
  "liveSassCompile.settings.formats": [
    {
      "format": "expanded",
      "extensionName": ".css",
      "savePath": "/"
    }
  ],
```

Change `"savePath": "/"` to `"savePath": "/styles"`, so it now looks like this:



```
{
  "liveSassCompile.settings.formats":[
    {
      "format": "expanded",
      "extensionName":".css",
      "savePath":"/styles",
    },

    // You can also use this minified extension for production, as it reduces the file size

    {
      "format": "compressed",
      "extensionName":".min.css",
      "savePath":"/styles",
    }
  ],
```

##### Step 3: Compile Sass



Now, after saving the settings, go back to the Sass file, and click on the button that says "Watch Sass" at the very bottom of the window.



![](https://i.imgur.com/N9bdPAx.png)

*Click on "Watch Sass"*



After you click the button, two files get created: `.css` and a `.css.map` in the `styles` folder.



You should not, however, change any of them. Because it already helps you compile the Sass into CSS every time you save new stylings.



###### Step 4: Link the CSS file

Then, link the CSS file in your `index.html`. In our case:



```html
    <link rel="stylesheet" href="/styles/main.css" />	
```



#### For Mac OS X or Linux

You will need [the Homebrew package manager](https://brew.sh/) and you can install Dart Sass by running

```bash
brew install sass/sass/sass
```



If you use **Node.js,** you can also install Sass using [npm](https://www.npmjs.com/) by running

```bash
npm install -g sass
```



**Note:** *this will install the* **pure JavaScript** *implementation of Sass, which runs somewhat* **slower** *than the other options listed here. But it has the* **same interface***, so it’ll be easy to swap in another implementation later if you need a bit more speed!*



Now we are all set up and ready, we can run the **Sass** executable to compile **.sass** or **.scss** files to **.css** files.

```
sass [sass/scss file path] [.css file path] 
```

For example, considering the `.scss` file and `.css` file are in the same folder, we can use the **-w** flag to autorun the command if any changes are detected in the `.scss` file.

```
sass ./styles/index.scss ./styles/index.css -w
```





### 2.4 Tips for using Sass

That was the complete introduction and installation process of Sass,as we have been focusing on Sass features like Nested Rules, Helper functions, Inheritance, Mixins, Partials, *etc*. 



Remember to review these good stuff for interviews for why using Sass



![](https://i.imgur.com/eQLnIsi.png)



As for interviews, you need to use at least 3 features of Sass. 
