# CSS Comprehensive Guide

## Table of Contents
1. [Introduction to CSS](#introduction-to-css)
2. [CSS Syntax](#css-syntax)
3. [CSS Selectors](#css-selectors)
4. [Box Model](#box-model)
5. [Typography](#typography)
6. [Colors](#colors)
7. [Layout](#layout)
8. [Positioning](#positioning)
9. [Flexbox](#flexbox)
10. [CSS Grid](#css-grid)
11. [Responsive Design](#responsive-design)
12. [Transitions and Animations](#transitions-and-animations)
13. [CSS Variables](#css-variables)
14. [Best Practices](#best-practices)

## Introduction to CSS

CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of HTML or XML documents. It controls the layout, appearance, and design of web pages.

**Ways to Include CSS:**

1. **Inline CSS** - Using the style attribute directly in HTML elements
```html
<p style="color: red; font-size: 18px;">This is a paragraph with inline CSS.</p>
```

2. **Internal CSS** - Using the `<style>` tag in the HTML document's `<head>` section
```html
<head>
  <style>
    p {
      color: blue;
      font-size: 16px;
    }
  </style>
</head>
```
3. **External CSS** - Linking to an external .css file
```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

## CSS Syntax

CSS consists of selectors and declarations:

```css
selector {
  property: value;
  property: value;
}
```

Example:
```css
p {
  color: blue;
  font-size: 16px;
}
```

## CSS Selectors

### Basic Selectors

1. **Element Selector** - Selects all instances of a specified element
```css
p {
  color: blue;
}
```

2. **Class Selector** - Selects elements with a specific class attribute
```css
.highlight {
  background-color: yellow;
}
```

3. **ID Selector** - Selects a single element with a specific ID
```css
#header {
  background-color: black;
  color: white;
}
```

4. **Universal Selector** - Selects all elements
```css
* {
  margin: 0;
  padding: 0;
}
```

### Combinators

1. **Descendant Selector** - Selects all elements that are descendants of a specified element
```css
div p {
  color: red;
}
```

2. **Child Selector** - Selects all elements that are direct children of a specified element
```css
div > p {
  color: green;
}
```
3. **Adjacent Sibling Selector** - Selects an element that is directly after another specific element
```css
h1 + p {
  font-weight: bold;
}
```

4. **General Sibling Selector** - Selects all elements that are siblings of a specified element
```css
h1 ~ p {
  color: purple;
}
```

### Attribute Selectors

```css
/* Selects elements with the specified attribute */
[title] {
  color: blue;
}

/* Selects elements where the attribute equals the value */
[type="text"] {
  border: 1px solid gray;
}

/* Selects elements where the attribute contains the value */
[class*="nav"] {
  font-weight: bold;
}
```

### Pseudo-classes and Pseudo-elements

**Pseudo-classes:**
```css
/* Style links on hover */
a:hover {
  text-decoration: underline;
}

/* Style the first child of an element */
li:first-child {
  font-weight: bold;
}

/* Style odd rows in a table */
tr:nth-child(odd) {
  background-color: #f2f2f2;
}
```

**Pseudo-elements:**
```css
/* Style the first line of a paragraph */
p::first-line {
  font-weight: bold;
}

/* Add content before an element */
h2::before {
  content: "→ ";
  color: blue;
}

/* Style the selection */
::selection {
  background-color: yellow;
  color: black;
}
```

## Box Model

Every element in HTML is a box that consists of:

- **Content** - The actual content (text, images, etc.)
- **Padding** - Space between the content and border
- **Border** - Line around the padding
- **Margin** - Space outside the border

```css
div {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  margin: 30px;
}
```

**Box-sizing Property:**
```css
/* Makes width and height include padding and border */
* {
  box-sizing: border-box;
}
```

## Typography

```css
p {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
  font-weight: bold;
  font-style: italic;
  line-height: 1.5;
  text-align: center;
  text-decoration: underline;
  text-transform: uppercase;
  letter-spacing: 2px;
  word-spacing: 5px;
}
```

**Web Fonts:**
```css
@font-face {
  font-family: 'MyCustomFont';
  src: url('fonts/custom-font.woff2') format('woff2');
}

body {
  font-family: 'MyCustomFont', sans-serif;
}
```

**Google Fonts:**
```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap">
```

```css
body {
  font-family: 'Roboto', sans-serif;
}
```
## Colors

### Color Values

```css
/* Color Names */
h1 {
  color: red;
}

/* Hex Colors */
h2 {
  color: #00ff00;
}

/* RGB Colors */
h3 {
  color: rgb(0, 0, 255);
}

/* RGBA Colors (with transparency) */
h4 {
  color: rgba(255, 0, 0, 0.5);
}

/* HSL Colors (Hue, Saturation, Lightness) */
h5 {
  color: hsl(240, 100%, 50%);
}

/* HSLA Colors (with transparency) */
h6 {
  color: hsla(240, 100%, 50%, 0.5);
}
```

### Background Properties

```css
div {
  background-color: #f0f0f0;
  background-image: url('image.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

/* Shorthand */
div {
  background: #f0f0f0 url('image.jpg') no-repeat center/cover;
}
```
### Gradients

```css
/* Linear Gradient */
.box {
  background: linear-gradient(to right, red, yellow);
}

/* Radial Gradient */
.circle {
  background: radial-gradient(circle, blue, green);
}
```

## Layout

### Display Property

```css
/* Block elements take full width */
div {
  display: block;
}

/* Inline elements only take necessary width */
span {
  display: inline;
}

/* Combination of block and inline */
nav a {
  display: inline-block;
  padding: 10px;
}

/* Grid container */
.container {
  display: grid;
}

/* Flexbox container */
.flex-container {
  display: flex;
}

/* Hide an element */
.hidden {
  display: none;
}
```

### Float and Clear

```css
/* Float elements to the left or right */
img {
  float: left;
  margin-right: 10px;
}

/* Clear floats */
.clearfix::after {
  content: "";
  clear: both;
  display: table;
}
```

## Positioning

```css
/* Static positioning (default) */
div {
  position: static;
}

/* Relative positioning */
.relative {
  position: relative;
  top: 20px;
  left: 30px;
}

/* Absolute positioning */
.absolute {
  position: absolute;
  top: 0;
  right: 0;
}

/* Fixed positioning */
.fixed {
  position: fixed;
  bottom: 20px;
  right: 20px;
}

/* Sticky positioning */
.sticky {
  position: sticky;
  top: 0;
}
```

## Flexbox

### Container Properties

```css
.flex-container {
  display: flex;
  flex-direction: row; /* row, row-reverse, column, column-reverse */
  flex-wrap: wrap; /* nowrap, wrap, wrap-reverse */
  justify-content: space-between; /* flex-start, flex-end, center, space-around, space-between, space-evenly */
  align-items: center; /* flex-start, flex-end, center, baseline, stretch */
  align-content: space-around; /* flex-start, flex-end, center, space-between, space-around, stretch */
  gap: 20px; /* space between flex items */
}
```
### Item Properties

```css
.flex-item {
  order: 2; /* default is 0 */
  flex-grow: 1; /* default is 0 */
  flex-shrink: 1; /* default is 1 */
  flex-basis: auto; /* default is auto */
  align-self: flex-end; /* overrides the container's align-items */
}

/* Shorthand */
.flex-item {
  flex: 1 1 auto; /* flex-grow flex-shrink flex-basis */
}
```

### Practical Flexbox Example

```html
<div class="card-container">
  <div class="card">
    <h3>Card 1</h3>
    <p>Card content goes here</p>
  </div>
  <div class="card">
    <h3>Card 2</h3>
    <p>Card content goes here</p>
  </div>
  <div class="card">
    <h3>Card 3</h3>
    <p>Card content goes here</p>
  </div>
</div>
```

```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
}

.card {
  flex: 0 1 300px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
```

## CSS Grid

### Container Properties

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr; /* three columns with different widths */
  grid-template-rows: 100px auto 100px; /* three rows with different heights */
  grid-gap: 20px; /* gap between grid items */
  /* or */
  gap: 20px;
  grid-template-areas: 
    "header header header"
    "sidebar main main"
    "footer footer footer";
}
```

### Item Properties

```css
.header {
  grid-area: header;
}

.sidebar {
  grid-area: sidebar;
}

.main {
  grid-area: main;
}

.footer {
  grid-area: footer;
}

.specific-item {
  grid-column: 1 / 3; /* start at column 1, end before column 3 */
  grid-row: 2 / 4; /* start at row 2, end before row 4 */
}
```

### Practical Grid Example

```html
<div class="layout">
  <header class="header">Header</header>
  <nav class="sidebar">Sidebar</nav>
  <main class="main">Main Content</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
.layout {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  min-height: 100vh;
  gap: 10px;
}

.header {
  grid-area: header;
  background-color: #f0f0f0;
  padding: 20px;
}

.sidebar {
  grid-area: sidebar;
  background-color: #e0e0e0;
  padding: 20px;
}

.main {
  grid-area: main;
  background-color: #f8f8f8;
  padding: 20px;
}

.footer {
  grid-area: footer;
  background-color: #f0f0f0;
  padding: 20px;
}
```
## Responsive Design

### Media Queries

```css
/* Styles for screens 768px and wider */
@media screen and (min-width: 768px) {
  .container {
    width: 750px;
  }
}

/* Styles for screens 992px and wider */
@media screen and (min-width: 992px) {
  .container {
    width: 970px;
  }
}

/* Styles for screens 1200px and wider */
@media screen and (min-width: 1200px) {
  .container {
    width: 1170px;
  }
}

/* Print styles */
@media print {
  .no-print {
    display: none;
  }
  body {
    font-size: 12pt;
  }
}
```

### Responsive Images

```css
img {
  max-width: 100%;
  height: auto;
}
```

### Viewport Meta Tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### Responsive Typography

```css
html {
  font-size: 16px;
}

h1 {
  font-size: 2rem; /* 32px */
}

@media (max-width: 768px) {
  html {
    font-size: 14px;
  }
  /* Now h1 will be 28px on smaller screens */
}
```

## Transitions and Animations

### Transitions

```css
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  transition: background-color 0.3s ease, transform 0.2s ease;
}

.button:hover {
  background-color: darkblue;
  transform: scale(1.05);
}
```
### Animations

```css
@keyframes slideIn {
  0% {
    transform: translateX(-100%);
    opacity: 0;
  }
  100% {
    transform: translateX(0);
    opacity: 1;
  }
}

.animated-element {
  animation: slideIn 1s ease-out forwards;
}
```

### Animation Properties

```css
.box {
  animation-name: bounce;
  animation-duration: 1s;
  animation-timing-function: ease;
  animation-delay: 0.5s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: forwards;
  animation-play-state: running;
}

/* Shorthand */
.box {
  animation: bounce 1s ease 0.5s infinite alternate forwards;
}
```

## CSS Variables

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2ecc71;
  --font-size-base: 16px;
  --spacing-unit: 8px;
}

.button {
  background-color: var(--primary-color);
  font-size: var(--font-size-base);
  padding: calc(var(--spacing-unit) * 2) calc(var(--spacing-unit) * 3);
}

.alert {
  border: 2px solid var(--secondary-color);
  margin-bottom: calc(var(--spacing-unit) * 3);
}

/* Variables can be scoped */
.dark-theme {
  --primary-color: #1a6aa2;
  --secondary-color: #25a25a;
}
```

## Best Practices

### Organization

```css
/* Group related styles */
/* Typography */
h1, h2, h3 {
  font-family: 'Georgia', serif;
}

/* Layout */
.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* Use comments to separate sections */
/* =========
   Header
   ========= */
header {
  /* header styles */
}

/* =========
   Footer
   ========= */
footer {
  /* footer styles */
}
```

### CSS Reset/Normalize

```css
/* Simple reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Or use a popular reset like normalize.css */
```
### CSS Specificity

Specificity hierarchy (from lowest to highest):
1. Element selectors (`p`, `div`)
2. Class selectors (`.class`), attribute selectors (`[type="text"]`), pseudo-classes (`:hover`)
3. ID selectors (`#id`)
4. Inline styles (`style="color: red"`)
5. `!important` (avoid when possible)

```css
/* Specificity: 0-0-1 */
p {
  color: blue;
}

/* Specificity: 0-1-0 */
.text {
  color: red;
}

/* Specificity: 0-1-1 */
p.text {
  color: green;
}

/* Specificity: 1-0-0 */
#unique {
  color: purple;
}

/* Avoid this when possible */
p {
  color: orange !important;
}
```

### BEM Naming Convention

BEM stands for Block, Element, Modifier:

```css
/* Block */
.card {
  background: white;
  border-radius: 4px;
}

/* Element (part of a block) */
.card__title {
  font-size: 18px;
  font-weight: bold;
}

.card__image {
  width: 100%;
}

/* Modifier (variation of a block or element) */
.card--featured {
  box-shadow: 0 0 10px rgba(0,0,0,0.2);
}

.card__title--large {
  font-size: 24px;
}
```

### Complete Practical Example

Here's a complete example of a simple card component using multiple CSS concepts:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CSS Card Example</title>
  <style>
    :root {
      --primary-color: #3498db;
      --secondary-color: #2ecc71;
      --text-color: #333;
      --light-bg: #f9f9f9;
      --border-radius: 8px;
      --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      --transition-speed: 0.3s;
    }
    
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      color: var(--text-color);
      background-color: #f0f0f0;
      padding: 20px;
    }
    
    .card-container {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
      max-width: 1200px;
      margin: 0 auto;
    }
    
    .card {
      flex: 1 1 300px;
      max-width: 350px;
      background-color: white;
      border-radius: var(--border-radius);
      overflow: hidden;
      box-shadow: var(--shadow);
      transition: transform var(--transition-speed), box-shadow var(--transition-speed);
    }
    
    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
    }
    
    .card__image {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }
    
    .card__content {
      padding: 20px;
    }
    
    .card__title {
      font-size: 1.5rem;
      margin-bottom: 10px;
      color: var(--primary-color);
    }
    
    .card__text {
      margin-bottom: 20px;
      color: #666;
    }
    
    .card__button {
      display: inline-block;
      background-color: var(--primary-color);
      color: white;
      padding: 10px 20px;
      border-radius: 4px;
      text-decoration: none;
      transition: background-color var(--transition-speed);
    }
    
    .card__button:hover {
      background-color: #2980b9;
    }
    
    .card--featured {
      border: 2px solid var(--secondary-color);
    }
    
    .card--featured .card__title {
      color: var(--secondary-color);
    }
    
    @media (max-width: 768px) {
      .card {
        flex: 1 1 100%;
        max-width: 100%;
      }
      
      .card__title {
        font-size: 1.3rem;
      }
    }
    
    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    .card {
      animation: fadeIn 0.5s ease-out forwards;
    }
    
    .card:nth-child(2) {
      animation-delay: 0.2s;
    }
    
    .card:nth-child(3) {
      animation-delay: 0.4s;
    }
  </style>
</head>
<body>
  <div class="card-container">
    <div class="card">
      <img src="https://via.placeholder.com/350x200" alt="Card image" class="card__image">
      <div class="card__content">
        <h2 class="card__title">Card Title</h2>
        <p class="card__text">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eget felis eget urna.</p>
        <a href="#" class="card__button">Read More</a>
      </div>
    </div>
    
    <div class="card card--featured">
      <img src="https://via.placeholder.com/350x200" alt="Featured card image" class="card__image">
      <div class="card__content">
        <h2 class="card__title">Featured Card</h2>
        <p class="card__text">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eget felis eget urna.</p>
        <a href="#" class="card__button">Read More</a>
      </div>
    </div>
    
    <div class="card">
      <img src="https://via.placeholder.com/350x200" alt="Card image" class="card__image">
      <div class="card__content">
        <h2 class="card__title">Another Card</h2>
        <p class="card__text">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam eget felis eget urna.</p>
        <a href="#" class="card__button">Read More</a>
      </div>
    </div>
  </div>
</body>
</html>
```

This example demonstrates:
- CSS variables
- Box model
- Flexbox layout
- Responsive design with media queries
- Transitions and animations
- BEM naming convention
- Hover effects
- CSS organization
