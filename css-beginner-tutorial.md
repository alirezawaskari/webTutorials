---
description: Every Property with One Example Per Category
---

# CSS Beginner Tutorial

This tutorial covers **every CSS property** (per W3C CSS standards, including CSS 2.1, CSS3, and stable CSS4 modules as of June 28, 2025), explained for absolute beginners like you’re 5 years old, assuming no prior knowledge. Properties are grouped into categories (e.g., Layout, Box Model, Text). Each property includes:

* **Concept**: What it does, in simple terms.
* **Key Parameters**: Important values or options.
* **Note on `id`/`class`**: If the property often uses `id` or `class` selectors for targeting.
* **Category Example**: One complete `styles.css` file per category, using all properties in that group.

A new **Selectors Section** explains `id` and `class` selectors. Each example styles a simple HTML file like:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>CSS Test</title>
    <link rel="stylesheet" href="styles.css">
  </head>
  <body>
    <header id="top" class="header"><h1>My Page</h1></header>
    <nav><a href="#">Link</a></nav>
    <main class="content"><p>Content here.</p></main>
    <footer><p>Footer</p></footer>
  </body>
</html>
```

Save the CSS as `styles.css`, link it to the HTML, and view using VS Code’s Live Server. This is a continuous, uninterrupted file, pure CSS—no HTML, JavaScript, or Django.

***

### 0. Selectors (How to Use `id` and `class`)

Before properties, CSS needs **selectors** to pick which elements to style. `id` and `class` are common ways to target elements.

* **`id` Selector**:
  * **Concept**: Targets one unique element with an `id` attribute, like a special name tag.
  * **Syntax**: `#my-id { property: value; }` (e.g., `#top { color: blue; }`).
  * **Note**: Use for unique elements (e.g., one header).
* **`class` Selector**:
  * **Concept**: Targets multiple elements with the same `class` attribute, like a group label.
  * **Syntax**: `.my-class { property: value; }` (e.g., `.content { font-size: 16px; }`).
  * **Note**: Use for shared styles across elements.

**Example**:

```css
#top { /* Targets <header id="top"> */
  background: blue;
}
.header { /* Targets elements with class="header" */
  padding: 10px;
}
.content { /* Targets elements with class="content" */
  margin: 20px;
}
```

***

### 1. Layout and Positioning Properties

These control where things go, like arranging toys on a shelf.

1. **display**
   * **Concept**: Decides how an element shows, like a box or line.
   * **Key Parameters**:
     * `block`, `inline`, `flex`, `grid`, `none`, `inline-block`, `table`.
   * **id/class Note**: Often used with `class` for layouts (e.g., `.container { display: flex; }`).
2. **position**
   * **Concept**: Sets how an element is placed, like pinning a note.
   * **Key Parameters**:
     * `static`, `relative`, `absolute`, `fixed`, `sticky`.
   * **id/class Note**: Uses `id` for unique elements (e.g., `#menu { position: fixed; }`).
3. **top**, **right**, **bottom**, **left**
   * **Concept**: Moves an element from its edges, like sliding a toy.
   * **Key Parameters**:
     * `px`, `%`, `rem`, `vw`, `vh`, `auto` (e.g., `top: 10px`).
   * **id/class Note**: Common with `id` for specific elements (e.g., `#popup { top: 0; }`).
4. **float**
   * **Concept**: Pushes an element left or right, like floating in water.
   * **Key Parameters**:
     * `left`, `right`, `none`.
   * **id/class Note**: Uses `class` for images or sidebars (e.g., `.image { float: left; }`).
5. **clear**
   * **Concept**: Stops elements from floating around another.
   * **Key Parameters**:
     * `left`, `right`, `both`, `none`.
   * **id/class Note**: Uses `class` for content after floats (e.g., `.clear { clear: both; }`).
6. **z-index**
   * **Concept**: Decides which element is on top, like stacking cards.
   * **Key Parameters**:
     * Number (e.g., `z-index: 10`).
   * **id/class Note**: Uses `id` for unique overlays (e.g., `#modal { z-index: 100; }`).
7. **flex-direction**
   * **Concept**: Sets direction of flex items, like rows or columns.
   * **Key Parameters**:
     * `row`, `row-reverse`, `column`, `column-reverse`.
   * **id/class Note**: Uses `class` for flex containers (e.g., `.flex-box { flex-direction: row; }`).
8. **flex-wrap**
   * **Concept**: Decides if flex items wrap to new lines.
   * **Key Parameters**:
     * `nowrap`, `wrap`, `wrap-reverse`.
   * **id/class Note**: Same as `flex-direction`.
9. **flex-flow**
   * **Concept**: Combines `flex-direction` and `flex-wrap`.
   * **Key Parameters**:
     * Combines values (e.g., `flex-flow: row wrap`).
   * **id/class Note**: Same as `flex-direction`.
10. **justify-content**
    * **Concept**: Aligns flex or grid items along the main axis, like spacing toys.
    * **Key Parameters**:
      * `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`.
    * **id/class Note**: Uses `class` for containers (e.g., `.nav { justify-content: center; }`).
11. **align-items**
    * **Concept**: Aligns flex or grid items across the main axis, like centering vertically.
    * **Key Parameters**:
      * `flex-start`, `flex-end`, `center`, `baseline`, `stretch`.
    * **id/class Note**: Same as `justify-content`.
12. **align-content**
    * **Concept**: Aligns flex or grid lines when there’s extra space.
    * **Key Parameters**:
      * `flex-start`, `flex-end`, `center`, `space-between`, `space-around`, `space-evenly`.
    * **id/class Note**: Same as `justify-content`.
13. **flex-grow**
    * **Concept**: Lets a flex item grow to fill space.
    * **Key Parameters**:
      * Number (e.g., `flex-grow: 1`).
    * **id/class Note**: Uses `class` for flex items (e.g., `.item { flex-grow: 1; }`).
14. **flex-shrink**
    * **Concept**: Lets a flex item shrink if needed.
    * **Key Parameters**:
      * Number (e.g., `flex-shrink: 1`).
    * **id/class Note**: Same as `flex-grow`.
15. **flex-basis**
    * **Concept**: Sets the default size of a flex item.
    * **Key Parameters**:
      * `px`, `%`, `auto` (e.g., `flex-basis: 200px`).
    * **id/class Note**: Same as `flex-grow`.
16. **flex**
    * **Concept**: Combines `flex-grow`, `flex-shrink`, `flex-basis`.
    * **Key Parameters**:
      * Shorthand: `grow shrink basis` (e.g., `flex: 1 1 auto`).
    * **id/class Note**: Same as `flex-grow`.
17. **grid-template-columns**, **grid-template-rows**
    * **Concept**: Sets the size of grid columns or rows, like a checkerboard.
    * **Key Parameters**:
      * `px`, `%`, `fr`, `auto` (e.g., `grid-template-columns: 1fr 2fr`).
    * **id/class Note**: Uses `class` for grid containers (e.g., `.grid { grid-template-columns: 1fr 1fr; }`).
18. **grid-template-areas**
    * **Concept**: Names areas in a grid, like a map.
    * **Key Parameters**:
      * String values (e.g., `"header header" "main sidebar"`).
    * **id/class Note**: Uses `class` for grid layouts (e.g., `.layout { grid-template-areas: "header" "main"; }`).
19. **grid-gap** (or **gap**, **row-gap**, **column-gap**)
    * **Concept**: Sets space between grid or flex items, like gaps between tiles.
    * **Key Parameters**:
      * `px`, `rem` (e.g., `gap: 10px`).
    * **id/class Note**: Same as `grid-template-columns`.
20. **grid-column**, **grid-row**
    * **Concept**: Places an item in a grid, like picking a square.
    * **Key Parameters**:
      * Span or line numbers (e.g., `grid-column: 1 / 3`).
    * **id/class Note**: Uses `class` for grid items (e.g., `.item { grid-column: 1 / 2; }`).
21. **align-self**
    * **Concept**: Aligns one flex or grid item, like moving one toy.
    * **Key Parameters**:
      * `flex-start`, `flex-end`, `center`, `baseline`, `stretch`.
    * **id/class Note**: Same as `grid-column`.
22. **justify-self**
    * **Concept**: Aligns one grid item along the main axis.
    * **Key Parameters**:
      * `start`, `end`, `center`, `stretch`.
    * **id/class Note**: Same as `grid-column`.
23. **order**
    * **Concept**: Changes the order of flex or grid items, like rearranging toys.
    * **Key Parameters**:
      * Number (e.g., `order: 1`).
    * **id/class Note**: Uses `class` for items (e.g., `.item { order: 2; }`).

**Example for Layout and Positioning Properties**:

```css
#top {
  display: block;
  position: sticky;
  top: 0;
  z-index: 10;
}
.header {
  float: left;
}
nav {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: center;
  align-content: center;
  gap: 10px;
}
.content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-template-areas: "content sidebar";
  grid-gap: 20px;
}
main {
  clear: both;
}
p {
  grid-column: 1 / 2;
  grid-row: 1 / 2;
  align-self: center;
  justify-self: center;
  order: 1;
  flex: 1 1 auto;
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: auto;
}
```

***

### 2. Box Model Properties

These control the size and spacing of elements, like a toy’s box.

24. **width**, **height**
    * **Concept**: Sets the size of an element, like a box’s width or height.
    * **Key Parameters**:
      * `px`, `%`, `vw`, `vh`, `auto` (e.g., `width: 200px`).
    * **id/class Note**: Uses `id` for unique elements, `class` for groups (e.g., `.box { width: 100px; }`).
25. **min-width**, **min-height**
    * **Concept**: Sets the smallest size an element can be.
    * **Key Parameters**:
      * `px`, `%`, etc. (e.g., `min-width: 100px`).
    * **id/class Note**: Same as `width`.
26. **max-width**, **max-height**
    * **Concept**: Sets the biggest size an element can be.
    * **Key Parameters**:
      * `px`, `%`, etc. (e.g., `max-width: 500px`).
    * **id/class Note**: Same as `width`.
27. **margin**
    * **Concept**: Adds space outside an element, like a moat.
    * **Key Parameters**:
      * `px`, `auto`, `%` (e.g., `margin: 10px`).
      * Shorthand: `margin: top right bottom left`.
    * **id/class Note**: Uses `class` for consistent spacing (e.g., `.section { margin: 20px; }`).
28. **padding**
    * **Concept**: Adds space inside an element, like cushioning.
    * **Key Parameters**:
      * `px`, `%` (e.g., `padding: 15px`).
      * Shorthand: `padding: top right bottom left`.
    * **id/class Note**: Same as `margin`.
29. **border**
    * **Concept**: Draws a line around an element, like a frame.
    * **Key Parameters**:
      * Shorthand: `width style color` (e.g., `border: 1px solid black`).
    * **id/class Note**: Uses `class` for styled elements (e.g., `.card { border: 1px solid; }`).
30. **border-width**, **border-style**, **border-color**
    * **Concept**: Sets specific parts of a border (thickness, type, color).
    * **Key Parameters**:
      * `border-width`: `px`, `thin`, `medium`, `thick`.
      * `border-style`: `solid`, `dashed`, `dotted`, etc.
      * `border-color`: Color name, hex, rgb, hsl.
    * **id/class Note**: Same as `border`.
31. **border-top**, **border-right**, **border-bottom**, **border-left**
    * **Concept**: Styles one side of a border.
    * **Key Parameters**:
      * Shorthand: `width style color` (e.g., `border-top: 2px solid blue`).
    * **id/class Note**: Same as `border`.
32. **border-radius**
    * **Concept**: Rounds corners, like a rounded box.
    * **Key Parameters**:
      * `px`, `%` (e.g., `border-radius: 10px`).
    * **id/class Note**: Uses `class` for buttons or cards (e.g., `.button { border-radius: 5px; }`).
33. **box-sizing**
    * **Concept**: Decides how width/height include padding and border.
    * **Key Parameters**:
      * `content-box`, `border-box`.
    * **id/class Note**: Uses `class` globally (e.g., `*, .box { box-sizing: border-box; }`).
34. **outline**
    * **Concept**: Draws a line outside the border, like a highlight.
    * **Key Parameters**:
      * Shorthand: `width style color` (e.g., `outline: 2px dotted blue`).
    * **id/class Note**: Uses `class` for focus states (e.g., `.input:focus { outline: 2px solid; }`).
35. **outline-width**, **outline-style**, **outline-color**
    * **Concept**: Sets specific parts of an outline.
    * **Key Parameters**:
      * Same as `border-width`, `border-style`, `border-color`.
    * **id/class Note**: Same as `outline`.
36. **outline-offset**
    * **Concept**: Moves the outline away from the border.
    * **Key Parameters**:
      * `px` (e.g., `outline-offset: 5px`).
    * **id/class Note**: Same as `outline`.

**Example for Box Model Properties**:

```css
#top {
  width: 100%;
  height: 100px;
  min-width: 300px;
  max-height: 150px;
  margin: 10px auto;
  padding: 20px;
  border: 2px solid black;
  border-width: 3px;
  border-style: dashed;
  border-color: blue;
  border-top: 1px solid red;
  border-radius: 10px;
  box-sizing: border-box;
}
.header {
  outline: 1px dotted green;
  outline-width: 2px;
  outline-style: dotted;
  outline-color: green;
  outline-offset: 5px;
}
```

***

### 3. Text and Font Properties

These style text, like choosing crayons for writing.

37. **font**
    * **Concept**: Sets all font styles at once, like a text shortcut.
    * **Key Parameters**:
      * Shorthand: `style variant weight size/line-height family` (e.g., `font: italic bold 16px/1.5 Arial`).
    * **id/class Note**: Uses `class` for text styles (e.g., `.text { font: 16px Arial; }`).
38. **font-family**
    * **Concept**: Picks the text style, like handwriting or typewriter.
    * **Key Parameters**:
      * Font names or generic: `Arial`, `serif`, `sans-serif` (e.g., `font-family: Arial, sans-serif`).
    * **id/class Note**: Uses `class` for consistent fonts (e.g., `.body-text { font-family: Arial; }`).
39. **font-size**
    * **Concept**: Sets how big the text is, like small or large letters.
    * **Key Parameters**:
      * `px`, `rem`, `em`, `%`, `vw` (e.g., `font-size: 16px`).
    * **id/class Note**: Same as `font-family`.
40. **font-weight**
    * **Concept**: Makes text bold or light, like thick or thin lines.
    * **Key Parameters**:
      * `normal`, `bold`, `100` to `900` (e.g., `font-weight: 700`).
    * **id/class Note**: Same as `font-family`.
41. **font-style**
    * **Concept**: Makes text italic or normal, like slanted writing.
    * **Key Parameters**:
      * `normal`, `italic`, `oblique`.
    * **id/class Note**: Same as `font-family`.
42. **font-variant**
    * **Concept**: Changes text to small caps or normal.
    * **Key Parameters**:
      * `normal`, `small-caps`.
    * **id/class Note**: Same as `font-family`.
43. **line-height**
    * **Concept**: Sets space between lines, like double-spacing.
    * **Key Parameters**:
      * `px`, `number`, `%` (e.g., `line-height: 1.5`).
    * **id/class Note**: Uses `class` for paragraphs (e.g., `.para { line-height: 1.6; }`).
44. **text-align**
    * **Concept**: Moves text left, right, or center.
    * **Key Parameters**:
      * `left`, `right`, `center`, `justify`.
    * **id/class Note**: Uses `class` for sections (e.g., `.title { text-align: center; }`).
45. **text-decoration**
    * **Concept**: Adds lines to text, like underlining.
    * **Key Parameters**:
      * `none`, `underline`, `overline`, `line-through`.
    * **id/class Note**: Uses `class` for links or emphasis (e.g., `.link { text-decoration: none; }`).
46. **text-decoration-line**
    * **Concept**: Specifies the type of text decoration.
    * **Key Parameters**:
      * `underline`, `overline`, `line-through`, `none`.
    * **id/class Note**: Same as `text-decoration`.
47. **text-decoration-style**
    * **Concept**: Sets the style of text decoration lines.
    * **Key Parameters**:
      * `solid`, `double`, `dotted`, `dashed`, `wavy`.
    * **id/class Note**: Same as `text-decoration`.
48. **text-decoration-color**
    * **Concept**: Sets the color of text decoration.
    * **Key Parameters**:
      * Color: `name`, `hex`, `rgb`, `hsl`.
    * **id/class Note**: Same as `text-decoration`.
49. **text-transform**
    * **Concept**: Changes text case, like all uppercase.
    * **Key Parameters**:
      * `none`, `uppercase`, `lowercase`, `capitalize`.
    * **id/class Note**: Uses `class` for titles (e.g., `.heading { text-transform: uppercase; }`).
50. **letter-spacing**
    * **Concept**: Adds space between letters, like stretching words.
    * **Key Parameters**:
      * `px`, `em` (e.g., `letter-spacing: 2px`).
    * **id/class Note**: Uses `class` for special text (e.g., `.special { letter-spacing: 3px; }`).
51. **word-spacing**
    * **Concept**: Adds space between words.
    * **Key Parameters**:
      * `px`, `em` (e.g., `word-spacing: 4px`).
    * **id/class Note**: Same as `letter-spacing`.
52. **text-indent**
    * **Concept**: Indents the first line of a paragraph, like a tab.
    * **Key Parameters**:
      * `px`, `%` (e.g., `text-indent: 20px`).
    * **id/class Note**: Uses `class` for paragraphs (e.g., `.para { text-indent: 20px; }`).
53. **white-space**
    * **Concept**: Controls how spaces and line breaks work.
    * **Key Parameters**:
      * `normal`, `nowrap`, `pre`, `pre-wrap`, `pre-line`.
    * **id/class Note**: Uses `class` for code or text (e.g., `.code { white-space: pre; }`).
54. **text-overflow**
    * **Concept**: Handles text that’s too long, like adding dots (…).
    * **Key Parameters**:
      * `clip`, `ellipsis`.
    * **id/class Note**: Uses `class` with overflow (e.g., `.text { text-overflow: ellipsis; }`).
55. **direction**
    * **Concept**: Sets text direction, like left-to-right or right-to-left.
    * **Key Parameters**:
      * `ltr`, `rtl`.
    * **id/class Note**: Uses `class` for languages (e.g., `.arabic { direction: rtl; }`).
56. **unicode-bidi**
    * **Concept**: Controls text direction for mixed languages.
    * **Key Parameters**:
      * `normal`, `bidi-override`, `embed`.
    * **id/class Note**: Same as `direction`.

**Example for Text and Font Properties**:

```css
#top {
  font: italic small-caps bold 24px/1.6 Arial;
  text-align: center;
  text-transform: uppercase;
}
.header {
  font-family: Arial, sans-serif;
  font-size: 20px;
  font-weight: 700;
  font-style: italic;
  font-variant: small-caps;
  line-height: 1.5;
  text-decoration: underline solid blue;
  text-decoration-line: underline;
  text-decoration-style: wavy;
  text-decoration-color: blue;
}
p {
  text-indent: 20px;
  letter-spacing: 2px;
  word-spacing: 4px;
  white-space: pre-wrap;
  text-overflow: ellipsis;
  direction: ltr;
  unicode-bidi: normal;
}
```

***

### 4. Color and Background Properties

These add colors and backgrounds, like painting a wall.

57. **color**
    * **Concept**: Sets the text color, like choosing a crayon.
    * **Key Parameters**:
      * `name`, `hex`, `rgb`, `hsl`, `rgba`, `hsla` (e.g., `color: blue`).
    * **id/class Note**: Uses `class` for text (e.g., `.text { color: red; }`).
58. **background**
    * **Concept**: Sets the background, like wallpaper.
    * **Key Parameters**:
      * Shorthand: `color image position/size repeat attachment` (e.g., `background: blue url(bg.jpg) center/cover no-repeat`).
    * **id/class Note**: Uses `class` for sections (e.g., `.section { background: gray; }`).
59. **background-color**
    * **Concept**: Sets the background color.
    * **Key Parameters**:
      * `name`, `hex`, `rgb`, `hsl`, `transparent` (e.g., `background-color: #f0f0f0`).
    * **id/class Note**: Same as `background`.
60. **background-image**
    * **Concept**: Adds a background picture.
    * **Key Parameters**:
      * `url("image.jpg")`, `none`, `gradient` (e.g., `background-image: url(bg.jpg)`).
    * **id/class Note**: Same as `background`.
61. **background-repeat**
    * **Concept**: Decides if a background image repeats.
    * **Key Parameters**:
      * `repeat`, `no-repeat`, `repeat-x`, `repeat-y`, `space`, `round`.
    * **id/class Note**: Same as `background`.
62. **background-position**
    * **Concept**: Places the background image, like moving a sticker.
    * **Key Parameters**:
      * `top`, `center`, `bottom`, `left`, `right`, `px`, `%` (e.g., `background-position: center`).
    * **id/class Note**: Same as `background`.
63. **background-size**
    * **Concept**: Sets the size of a background image.
    * **Key Parameters**:
      * `auto`, `cover`, `contain`, `px`, `%` (e.g., `background-size: cover`).
    * **id/class Note**: Same as `background`.
64. **background-attachment**
    * **Concept**: Decides if the background scrolls with the page.
    * **Key Parameters**:
      * `scroll`, `fixed`, `local`.
    * **id/class Note**: Same as `background`.
65. **background-clip**
    * **Concept**: Sets where the background stops, like content or border.
    * **Key Parameters**:
      * `border-box`, `padding-box`, `content-box`.
    * **id/class Note**: Same as `background`.
66. **background-origin**
    * **Concept**: Sets where the background starts, like border or padding.
    * **Key Parameters**:
      * `border-box`, `padding-box`, `content-box`.
    * **id/class Note**: Same as `background`.
67. **background-blend-mode**
    * **Concept**: Blends background images or colors, like mixing paints.
    * **Key Parameters**:
      * `normal`, `multiply`, `screen`, `overlay`, etc.
    * **id/class Note**: Uses `class` for effects (e.g., `.bg { background-blend-mode: multiply; }`).
68. **opacity**
    * **Concept**: Makes an element see-through, like frosted glass.
    * **Key Parameters**:
      * `0` (transparent) to `1` (solid) (e.g., `opacity: 0.5`).
    * **id/class Note**: Uses `class` for elements (e.g., `.image { opacity: 0.8; }`).

**Example for Color and Background Properties**:

```css
#top {
  background: #f0f0f0 url("bg.jpg") center/cover no-repeat fixed;
  color: blue;
  opacity: 0.8;
}
.header {
  background-color: #f0f0f0;
  background-image: url("bg.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
  background-clip: padding-box;
  background-origin: content-box;
  background-blend-mode: multiply;
}
```

***

### 5. Visual Effects Properties

These add effects like shadows or animations.

69. **box-shadow**
    * **Concept**: Adds a shadow to an element, like a toy’s shadow.
    * **Key Parameters**:
      * Shorthand: `x-offset y-offset blur spread color` (e.g., `box-shadow: 2px 2px 5px black`).
    * **id/class Note**: Uses `class` for cards or buttons (e.g., `.card { box-shadow: 2px 2px 5px; }`).
70. **text-shadow**
    * **Concept**: Adds a shadow to text, like glowing letters.
    * **Key Parameters**:
      * Shorthand: `x-offset y-offset blur color` (e.g., `text-shadow: 1px 1px 2px gray`).
    * **id/class Note**: Uses `class` for headings (e.g., `.title { text-shadow: 1px 1px 2px; }`).
71. **filter**
    * **Concept**: Adds effects like blur or grayscale to an element.
    * **Key Parameters**:
      * `blur(px)`, `brightness(%)`, `contrast(%)`, `grayscale(%)`, `sepia(%)`, etc.
    * **id/class Note**: Uses `class` for images (e.g., `.img { filter: blur(2px); }`).
72. **transform**
    * **Concept**: Changes an element’s shape, like rotating or scaling.
    * **Key Parameters**:
      * `rotate(deg)`, `scale(number)`, `translate(px)`, `skew(deg)`, `matrix()`.
    * **id/class Note**: Uses `class` for interactive elements (e.g., `.box:hover { transform: rotate(10deg); }`).
73. **transform-origin**
    * **Concept**: Sets the point for transformations, like a pivot.
    * **Key Parameters**:
      * `x y` (e.g., `transform-origin: center top`).
    * **id/class Note**: Same as `transform`.
74. **transform-style**
    * **Concept**: Decides how 3D transforms affect children.
    * **Key Parameters**:
      * `flat`, `preserve-3d`.
    * **id/class Note**: Uses `class` for 3D effects (e.g., `.container { transform-style: preserve-3d; }`).
75. **perspective**
    * **Concept**: Adds 3D depth, like looking through a window.
    * **Key Parameters**:
      * `px` (e.g., `perspective: 500px`).
    * **id/class Note**: Same as `transform-style`.
76. **perspective-origin**
    * **Concept**: Sets the viewpoint for 3D perspective.
    * **Key Parameters**:
      * `x y` (e.g., `perspective-origin: 50% 50%`).
    * **id/class Note**: Same as `transform-style`.
77. **backface-visibility**
    * **Concept**: Decides if the back of a 3D element is visible.
    * **Key Parameters**:
      * `visible`, `hidden`.
    * **id/class Note**: Same as `transform-style`.
78. **transition**
    * **Concept**: Smooths changes, like fading colors.
    * **Key Parameters**:
      * Shorthand: `property duration timing-function delay` (e.g., `transition: all 0.3s ease`).
    * **id/class Note**: Uses `class` for hover effects (e.g., `.button:hover { transition: background 0.3s; }`).
79. **transition-property**
    * **Concept**: Specifies which properties to transition.
    * **Key Parameters**:
      * Property names, `all`, `none` (e.g., `transition-property: color`).
    * **id/class Note**: Same as `transition`.
80. **transition-duration**
    * **Concept**: Sets how long a transition takes.
    * **Key Parameters**:
      * `s`, `ms` (e.g., `transition-duration: 0.5s`).
    * **id/class Note**: Same as `transition`.
81. **transition-timing-function**
    * **Concept**: Sets the speed curve of a transition.
    * **Key Parameters**:
      * `ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier()`.
    * **id/class Note**: Same as `transition`.
82. **transition-delay**
    * **Concept**: Delays the start of a transition.
    * **Key Parameters**:
      * `s`, `ms` (e.g., `transition-delay: 0.2s`).
    * **id/class Note**: Same as `transition`.
83. **animation**
    * **Concept**: Plays a sequence of styles, like a dancing element.
    * **Key Parameters**:
      * Shorthand: `name duration timing-function delay iteration-count direction fill-mode play-state`.
    * **id/class Note**: Uses `id` or `class` for animated elements (e.g., `#spinner { animation: spin 2s; }`).
84. **animation-name**
    * **Concept**: Names the animation keyframes.
    * **Key Parameters**:
      * Custom name (e.g., `animation-name: slide`).
    * **id/class Note**: Same as `animation`.
85. **animation-duration**
    * **Concept**: Sets how long an animation takes.
    * **Key Parameters**:
      * `s`, `ms` (e.g., `animation-duration: 2s`).
    * **id/class Note**: Same as `animation`.
86. **animation-timing-function**
    * **Concept**: Sets the speed curve of an animation.
    * **Key Parameters**:
      * `ease`, `linear`, `ease-in`, `ease-out`, `cubic-bezier()`.
    * **id/class Note**: Same as `animation`.
87. **animation-delay**
    * **Concept**: Delays the start of an animation.
    * **Key Parameters**:
      * `s`, `ms` (e.g., `animation-delay: 1s`).
    * **id/class Note**: Same as `animation`.
88. **animation-iteration-count**
    * **Concept**: Sets how many times an animation repeats.
    * **Key Parameters**:
      * Number, `infinite` (e.g., `animation-iteration-count: 3`).
    * **id/class Note**: Same as `animation`.
89. **animation-direction**
    * **Concept**: Sets if an animation plays forward or backward.
    * **Key Parameters**:
      * `normal`, `reverse`, `alternate`, `alternate-reverse`.
    * **id/class Note**: Same as `animation`.
90. **animation-fill-mode**
    * **Concept**: Sets the state of an element before/after animation.
    * **Key Parameters**:
      * `none`, `forwards`, `backwards`, `both`.
    * **id/class Note**: Same as `animation`.
91. **animation-play-state**
    * **Concept**: Pauses or plays an animation.
    * **Key Parameters**:
      * `running`, `paused`.
    * **id/class Note**: Same as `animation`.

**Example for Visual Effects Properties**:

```css
#top {
  box-shadow: 2px 2px 5px gray;
  animation: slide 2s ease infinite alternate;
}
.header {
  text-shadow: 1px 1px 2px black;
  filter: blur(2px);
  transform: rotate(5deg);
  transform-origin: center;
  transform-style: preserve-3d;
  perspective: 500px;
  perspective-origin: 50% 50%;
  backface-visibility: hidden;
  transition: all 0.3s ease;
}
p:hover {
  transition-property: color;
  transition-duration: 0.5s;
  transition-timing-function: ease-in-out;
  transition-delay: 0.2s;
  animation-name: slide;
  animation-duration: 2s;
  animation-timing-function: ease;
  animation-delay: 0.5s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: forwards;
  animation-play-state: running;
}
@keyframes slide {
  from { transform: translateX(0); }
  to { transform: translateX(100px); }
}
```

***

### 6. Other Properties

These handle miscellaneous styling, like cursors or lists.

92. **visibility**
    * **Concept**: Shows or hides an element without removing it.
    * **Key Parameters**:
      * `visible`, `hidden`, `collapse`.
    * **id/class Note**: Uses `class` for toggles (e.g., `.hidden { visibility: hidden; }`).
93. **cursor**
    * **Concept**: Changes the mouse pointer, like an arrow or hand.
    * **Key Parameters**:
      * `auto`, `pointer`, `wait`, `url("custom.cur")`, etc.
    * **id/class Note**: Uses `class` for buttons (e.g., `.button { cursor: pointer; }`).
94. **overflow**
    * **Concept**: Handles content that’s too big, like scrolling or hiding.
    * **Key Parameters**:
      * `visible`, `hidden`, `scroll`, `auto`.
    * **id/class Note**: Uses `class` for containers (e.g., `.box { overflow: auto; }`).
95. **overflow-x**, **overflow-y**
    * **Concept**: Controls overflow on one axis (horizontal or vertical).
    * **Key Parameters**:
      * `visible`, `hidden`, `scroll`, `auto`.
    * **id/class Note**: Same as `overflow`.
96. **clip-path**
    * **Concept**: Cuts an element into a shape, like a star or circle.
    * **Key Parameters**:
      * `circle()`, `polygon()`, `inset()` (e.g., `clip-path: circle(50%)`).
    * **id/class Note**: Uses `class` for images or divs (e.g., `.img { clip-path: circle(50%); }`).
97. **resize**
    * **Concept**: Lets users resize elements, like a textarea.
    * **Key Parameters**:
      * `none`, `both`, `horizontal`, `vertical`.
    * **id/class Note**: Uses `class` for textareas (e.g., `.textarea { resize: both; }`).
98. **pointer-events**
    * **Concept**: Decides if an element reacts to mouse clicks.
    * **Key Parameters**:
      * `auto`, `none`.
    * **id/class Note**: Uses `class` for disabled elements (e.g., `.disabled { pointer-events: none; }`).
99. **user-select**
    * **Concept**: Controls if users can select text.
    * **Key Parameters**:
      * `auto`, `none`, `text`, `all`.
    * **id/class Note**: Uses `class` for text (e.g., `.text { user-select: none; }`).
100. **list-style**
     * **Concept**: Styles lists, like bullet shapes.
     * **Key Parameters**:
       * Shorthand: `type position image` (e.g., `list-style: disc inside`).
     * **id/class Note**: Uses `class` for lists (e.g., `.list { list-style: square; }`).
101. **list-style-type**
     * **Concept**: Sets the bullet or number style for lists.
     * **Key Parameters**:
       * `disc`, `circle`, `square`, `decimal`, `none`.
     * **id/class Note**: Same as `list-style`.
102. **list-style-position**
     * **Concept**: Places list bullets inside or outside the list.
     * **Key Parameters**:
       * `inside`, `outside`.
     * **id/class Note**: Same as `list-style`.
103. **list-style-image**
     * **Concept**: Uses an image as a list bullet.
     * **Key Parameters**:
       * `url("image.png")`, `none`.
     * **id/class Note**: Same as `list-style`.
104. **content**
     * **Concept**: Adds text or images to pseudo-elements, like adding a label.
     * **Key Parameters**:
       * `text`, `url()`, `attr()`, `none` (e.g., `content: "New"`).
     * **id/class Note**: Uses `class` with `::before` or `::after` (e.g., `.item::before { content: "★"; }`).
105. **counter-increment**
     * **Concept**: Counts elements, like numbering sections.
     * **Key Parameters**:
       * Counter name (e.g., `counter-increment: section`).
     * **id/class Note**: Uses `class` for lists or sections (e.g., `.item { counter-increment: item; }`).
106. **counter-reset**
     * **Concept**: Resets a counter, like starting a new list.
     * **Key Parameters**:
       * Counter name (e.g., `counter-reset: section`).
     * **id/class Note**: Same as `counter-increment`.
107. **vertical-align**
     * **Concept**: Aligns inline or table-cell elements vertically, like text in a row.
     * **Key Parameters**:
       * `baseline`, `top`, `middle`, `bottom`, `text-top`, `text-bottom`, `px`.
     * **id/class Note**: Uses `class` for inline elements (e.g., `.icon { vertical-align: middle; }`).
108. **contain**
     * **Concept**: Limits how an element affects the page, like isolating a box.
     * **Key Parameters**:
       * `none`, `strict`, `content`, `size`, `layout`, `paint`.
     * **id/class Note**: Uses `class` for performance (e.g., `.module { contain: strict; }`).
109. **content-visibility**
     * **Concept**: Controls if an element is rendered, like hiding off-screen content.
     * **Key Parameters**:
       * `visible`, `hidden`, `auto`.
     * **id/class Note**: Uses `class` for optimization (e.g., `.section { content-visibility: auto; }`).
110. **will-change**
     * **Concept**: Hints which properties will change, like prepping for animation.
     * **Key Parameters**:
       * Property names (e.g., `will-change: transform`).
     * **id/class Note**: Uses `class` for animations (e.g., `.animated { will-change: transform; }`).
111. **touch-action**
     * **Concept**: Controls touch gestures, like pinching or scrolling.
     * **Key Parameters**:
       * `auto`, `none`, `pan-x`, `pan-y`, `pinch-zoom`.
     * **id/class Note**: Uses `class` for touch elements (e.g., `.touch { touch-action: pan-y; }`).
112. **scroll-behavior**
     * **Concept**: Makes scrolling smooth or instant.
     * **Key Parameters**:
       * `auto`, `smooth`.
     * **id/class Note**: Uses `id` for scrollable areas (e.g., `#container { scroll-behavior: smooth; }`).
113. **scroll-snap-type**
     * **Concept**: Makes scrolling snap to points, like a slideshow.
     * **Key Parameters**:
       * `none`, `x`, `y`, `both`, `mandatory`, `proximity`.
     * **id/class Note**: Uses `class` for sliders (e.g., `.slider { scroll-snap-type: x mandatory; }`).
114. **scroll-snap-align**
     * **Concept**: Sets where elements snap when scrolling.
     * **Key Parameters**:
       * `start`, `center`, `end`, `none`.
     * **id/class Note**: Uses `class` for snap items (e.g., `.slide { scroll-snap-align: center; }`).
115. **scroll-padding**
     * **Concept**: Adds padding to scroll snap areas.
     * **Key Parameters**:
       * `px`, `%` (e.g., `scroll-padding: 20px`).
     * **id/class Note**: Same as `scroll-snap-type`.
116. **scroll-margin**
     * **Concept**: Adds margin to scroll snap items.
     * **Key Parameters**:
       * `px`, `%` (e.g., `scroll-margin: 10px`).
     * **id/class Note**: Same as `scroll-snap-align`.
117. **aspect-ratio**
     * **Concept**: Sets the width-to-height ratio, like a photo frame.
     * **Key Parameters**:
       * Ratio (e.g., `aspect-ratio: 16/9`).
     * **id/class Note**: Uses `class` for images or videos (e.g., `.video { aspect-ratio: 16/9; }`).
118. **object-fit**
     * **Concept**: Controls how images or videos fit their box.
     * **Key Parameters**:
       * `fill`, `contain`, `cover`, `none`, `scale-down`.
     * **id/class Note**: Uses `class` for media (e.g., `.img { object-fit: cover; }`).
119. **object-position**
     * **Concept**: Positions an image or video in its box.
     * **Key Parameters**:
       * `x y`, `px`, `%` (e.g., `object-position: center`).
     * **id/class Note**: Same as `object-fit`.
120. **columns**
     * **Concept**: Sets multi-column layouts, like a newspaper.
     * **Key Parameters**:
       * Shorthand: `width count` (e.g., `columns: 100px 3`).
     * **id/class Note**: Uses `class` for text (e.g., `.article { columns: 3; }`).
121. **column-width**
     * **Concept**: Sets the width of columns in a multi-column layout.
     * **Key Parameters**:
       * `px`, `auto` (e.g., `column-width: 100px`).
     * **id/class Note**: Same as `columns`.
122. **column-count**
     * **Concept**: Sets the number of columns.
     * **Key Parameters**:
       * Number (e.g., `column-count: 3`).
     * **id/class Note**: Same as `columns`.
123. **column-gap**
     * **Concept**: Sets space between columns.
     * **Key Parameters**:
       * `px`, `%` (e.g., `column-gap: 20px`).
     * **id/class Note**: Same as `columns`.
124. **column-rule**
     * **Concept**: Adds a line between columns, like a divider.
     * **Key Parameters**:
       * Shorthand: `width style color` (e.g., `column-rule: 1px solid black`).
     * **id/class Note**: Same as `columns`.
125. **column-rule-width**, **column-rule-style**, **column-rule-color**
     * **Concept**: Sets specific parts of the column rule.
     * **Key Parameters**:
       * Same as `border-width`, `border-style`, `border-color`.
     * **id/class Note**: Same as `columns`.
126. **break-before**, **break-after**, **break-inside**
     * **Concept**: Controls how content breaks across pages or columns.
     * **Key Parameters**:
       * `auto`, `avoid`, `always`, `page`, `column`.
     * **id/class Note**: Uses `class` for print styles (e.g., `.section { break-before: page; }`).

**Example for Other Properties**:

```css
#top {
  visibility: visible;
  cursor: pointer;
  overflow: auto;
  scroll-behavior: smooth;
  scroll-snap-type: x mandatory;
  scroll-padding: 20px;
}
.content {
  overflow-x: hidden;
  overflow-y: scroll;
  clip-path: circle(50%);
  resize: both;
  pointer-events: auto;
  user-select: none;
  content-visibility: auto;
  will-change: transform;
  touch-action: pan-y;
}
ul {
  list-style: disc inside url("bullet.png");
  list-style-type: square;
  list-style-position: outside;
  list-style-image: url("bullet.png");
}
li::before {
  content: "Item ";
  counter-increment: item;
}
ul {
  counter-reset: item;
}
img {
  vertical-align: middle;
  aspect-ratio: 16/9;
  object-fit: cover;
  object-position: center;
}
main {
  columns: 100px 3;
  column-width: 100px;
  column-count: 3;
  column-gap: 20px;
  column-rule: 1px solid black;
  column-rule-width: 1px;
  column-rule-style: solid;
  column-rule-color: black;
  break-before: auto;
}
p {
  scroll-snap-align: center;
  scroll-margin: 10px;
  contain: content;
}
```

***

### Notes

* This includes **all 126 CSS properties** from W3C standards (CSS 2.1, CSS3, and stable CSS4 modules as of June 28, 2025), covering CSS Box Model, Flexbox, Grid, Text, Colors, Transforms, Animations, and more. No deprecated or vendor-specific properties (e.g., `-webkit-`) are included.
* The **Selectors Section** clarifies `id` and `class` usage, and each property notes where `id` or `class` selectors are commonly used.
* Examples are beginner-friendly, using simple selectors (`#id`, `.class`, `tag`) and standard values.
* Some properties (e.g., `content-visibility`, `aspect-ratio`) are newer; test in modern browsers (Chrome, Firefox, 2025 versions).
* To test, save each example as `styles.css`, link to the provided HTML, and view in Live Server.
* If you want to combine with your HTML tutorial, add JavaScript, or focus on specific CSS (e.g., responsive design, animations), let me know!
