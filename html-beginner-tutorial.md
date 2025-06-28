---
description: Every Tag with One Example Per Category
---

# HTML Beginner Tutorial

This tutorial covers **every HTML5 tag** (per W3C standards as of June 28, 2025), explained for absolute beginners like you’re 5 years old, assuming no prior knowledge. Tags are grouped into categories (e.g., Document Structure, Semantic, Text, etc.). Each tag includes:

* **Concept**: What it does, in simple terms.
* **Key Parameters**: Important attributes to customize it.
* **Category Example**: One complete HTML file per category, using all tags in that group.

Save each category’s example as `index.html` and view using VS Code’s Live Server. This is one continuous, uninterrupted file, focusing only on HTML—no Django, CSS, JavaScript, or other tech, as requested.

***

### 1. Document Structure Tags

These tags build the basic structure of a webpage, like the foundation of a house.

1. **`<!DOCTYPE html>`**
   * **Concept**: Tells the browser, “This is a modern webpage!” Like a sticker saying “HTML5.”
   * **Key Parameters**: None.
2. **`<html>`**
   * **Concept**: The big box holding your whole webpage, like a toy chest.
   * **Key Parameters**:
     * `lang`: Sets the language (e.g., `lang="en"`).
     * `id`, `class`: For naming parts.
3. **`<head>`**
   * **Concept**: Holds hidden info, like the page’s title, that the browser needs.
   * **Key Parameters**:
     * `id`, `class`: Rarely used.
4. **`<body>`**
   * **Concept**: Shows all visible stuff, like text or pictures.
   * **Key Parameters**:
     * `id`, `class`: For naming parts.
5. **`<base>`**
   * **Concept**: Sets a starting point for all links, like a home address.
   * **Key Parameters**:
     * `href`: Base URL (e.g., `href="https://example.com/"`).
     * `target`: Where links open (e.g., `target="_blank"`).
6. **`<link>`**
   * **Concept**: Connects to files like stylesheets, like adding decorations.
   * **Key Parameters**:
     * `rel`: Relationship (e.g., `rel="stylesheet"`).
     * `href`: File path.
     * `type`: File type (e.g., `type="text/css"`).
7. **`<meta>`**
   * **Concept**: Adds info about the page, like how to read text.
   * **Key Parameters**:
     * `charset`: Text encoding (e.g., `charset="UTF-8"`).
     * `name`, `content`: For info (e.g., `name="description" content="My page"`).
     * `http-equiv`: Browser instructions (e.g., `http-equiv="refresh"`).
8. **`<style>`**
   * **Concept**: Adds styles (like colors) right in the HTML.
   * **Key Parameters**:
     * `type`: Usually `type="text/css"`.
     * `media`: For specific devices (e.g., `media="screen"`).
9. **`<title>`**
   * **Concept**: Names the page in the browser tab.
   * **Key Parameters**: None.
10. **`<script>`**
    * **Concept**: Adds code to make things interactive.
    * **Key Parameters**:
      * `src`: Script file (e.g., `src="main.js"`).
      * `defer`: Waits to run.
      * `async`: Runs right away.
      * `type`: Script type (e.g., `type="text/javascript"`).
11. **`<noscript>`**
    * **Concept**: Shows a message if code can’t run.
    * **Key Parameters**: None.

**Example for Document Structure Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <base href="https://example.com/" target="_blank">
    <meta charset="UTF-8">
    <meta name="description" content="A simple page">
    <link rel="stylesheet" href="styles.css" type="text/css">
    <style type="text/css">
      body { font-family: Arial; }
    </style>
    <title>My Page</title>
    <script src="main.js" defer></script>
    <noscript>Please enable JavaScript.</noscript>
  </head>
  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

***

### 2. Semantic Tags

These tags give meaning to parts of your page, like labeling a header or footer.

12. **`<header>`**
    * **Concept**: The top of your page, like a book’s cover with a title or menu.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
      * `aria-label`: For accessibility (e.g., `aria-label="Page header"`).
13. **`<nav>`**
    * **Concept**: A menu with links, like a map to explore your page.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
      * `aria-label`: Names the menu (e.g., `aria-label="Navigation"`).
14. **`<main>`**
    * **Concept**: The main stuff on your page, like the story in a book.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
      * `aria-label`: Describes content (e.g., `aria-label="Main content"`).
15. **`<article>`**
    * **Concept**: A complete piece, like a story or post.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
16. **`<section>`**
    * **Concept**: Groups related content, like chapters.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
      * `aria-label`: Describes the section.
17. **`<aside>`**
    * **Concept**: Extra info, like a sidebar with fun facts.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
18. **`<footer>`**
    * **Concept**: The bottom of your page, like contact info.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
19. **`<details>`**
    * **Concept**: A box that hides content until clicked, like a secret door.
    * **Key Parameters**:
      * `open`: Shows content by default.
      * `id`, `class`: For naming parts.
20. **`<summary>`**
    * **Concept**: The clickable title for a `<details>` box.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
21. **`<figure>`**
    * **Concept**: Holds pictures or videos with a caption, like a framed photo.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
22. **`<figcaption>`**
    * **Concept**: The caption for a `<figure>`, like a label.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
23. **`<dialog>`**
    * **Concept**: A pop-up box, like an alert message.
    * **Key Parameters**:
      * `open`: Shows the dialog.
      * `id`, `class`: For naming parts.

**Example for Semantic Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>My Story Page</title>
  </head>
  <body>
    <header aria-label="Page header">
      <h1>My Stories</h1>
      <nav aria-label="Navigation">
        <a href="/home">Home</a>
        <a href="/about">About</a>
      </nav>
    </header>
    <main aria-label="Main content">
      <article>
        <h2>A Fun Story</h2>
        <p>Once upon a time...</p>
      </article>
      <section aria-label="More stories">
        <h2>Other Stories</h2>
        <p>Read more tales!</p>
      </section>
      <aside>
        <p>Fun fact: I love books!</p>
      </aside>
      <figure>
        <img src="story.jpg" alt="Story image">
        <figcaption>A book cover</figcaption>
      </figure>
      <details>
        <summary>More Info</summary>
        <p>Secret story details!</p>
      </details>
      <dialog open>
        <p>Welcome to my page!</p>
      </dialog>
    </main>
    <footer>
      <p>Contact: me@example.com</p>
    </footer>
  </body>
</html>
```

***

### 3. Text and Inline Tags

These tags format text or add small bits of content.

24. **`<h1>` to `<h6>`**
    * **Concept**: Headings, like titles (1 is biggest, 6 is smallest).
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
25. **`<p>`**
    * **Concept**: A paragraph of text, like a story block.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
26. **`<a>`**
    * **Concept**: A link to another page, like a door.
    * **Key Parameters**:
      * `href`: Destination URL.
      * `target`: Where it opens (e.g., `target="_blank"`).
      * `rel`: Link type (e.g., `rel="noopener"`).
27. **`<span>`**
    * **Concept**: A small piece of text for styling, like highlighting a word.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
28. **`<strong>`**
    * **Concept**: Makes text bold and important, like shouting.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
29. **`<em>`**
    * **Concept**: Makes text italic and emphasized, like stressing a word.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
30. **`<b>`**
    * **Concept**: Makes text bold just for looks.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
31. **`<i>`**
    * **Concept**: Makes text italic just for looks.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
32. **`<u>`**
    * **Concept**: Underlines text, like in a notebook.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
33. **`<mark>`**
    * **Concept**: Highlights text, like using a marker.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
34. **`<small>`**
    * **Concept**: Makes text smaller, like fine print.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
35. **`<del>`**
    * **Concept**: Crosses out text, like it’s deleted.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
36. **`<ins>`**
    * **Concept**: Underlines text, like it’s newly added.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
37. **`<sub>`**
    * **Concept**: Puts text lower, like for H₂O.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
38. **`<sup>`**
    * **Concept**: Puts text higher, like for x².
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
39. **`<q>`**
    * **Concept**: Puts quotes around text, like a short quote.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
40. **`<blockquote>`**
    * **Concept**: Shows a big quote, like a paragraph from someone.
    * **Key Parameters**:
      * `cite`: Source URL.
      * `id`, `class`: For naming parts.
41. **`<abbr>`**
    * **Concept**: Shows a short form of a word, like “HTML.”
    * **Key Parameters**:
      * `title`: Full word (e.g., `title="HyperText Markup Language"`).
      * `id`, `class`: For naming parts.
42. **`<cite>`**
    * **Concept**: Names a source, like a book or movie.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
43. **`<time>`**
    * **Concept**: Shows a date or time for computers.
    * **Key Parameters**:
      * `datetime`: Machine-readable date (e.g., `datetime="2025-06-28"`).
      * `id`, `class`: For naming parts.
44. **`<code>`**
    * **Concept**: Shows computer code, like `x = 1`.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
45. **`<pre>`**
    * **Concept**: Keeps spaces and lines in text, like typed code.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
46. **`<kbd>`**
    * **Concept**: Shows keyboard keys, like `Enter`.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
47. **`<samp>`**
    * **Concept**: Shows computer output, like “Error.”
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
48. **`<var>`**
    * **Concept**: Shows a variable, like `x` in math.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.

**Example for Text and Inline Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Text Page</title>
  </head>
  <body>
    <h1>Big Title</h1>
    <h2>Smaller Title</h2>
    <h3>Section</h3>
    <p>This is my <strong>important</strong> story about <em>fun</em>.</p>
    <p>I <b>love</b> to <i>write</i> and <u>underline</u> <mark>key</mark> words.</p>
    <p>I <del>erased</del> and <ins>added</ins> text.</p>
    <p>Water is H<sub>2</sub>O, and 2<sup>3</sup> is 8.</p>
    <p>She said <q>Write more</q>.</p>
    <blockquote cite="https://example.com">Stories are magic.</blockquote>
    <p>Learn <abbr title="HyperText Markup Language">HTML</abbr> from <cite>Story Book</cite>.</p>
    <p>Posted on <time datetime="2025-06-28">June 28, 2025</time>.</p>
    <p>Use <code>let x = 1;</code> in code.</p>
    <pre>
      function sayHi() {
        console.log("Hello");
      }
    </pre>
    <p>Press <kbd>Ctrl</kbd> to save, expect <samp>Done</samp>.</p>
    <p>Variable <var>y</var> holds data.</p>
    <span>Special text</span>
    <p><small>Fine print here.</small></p>
    <a href="/more" rel="noopener">Read more</a>
  </body>
</html>
```

***

### 4. Lists and Tables

These tags organize content in lists or grids.

49. **`<ul>`**
    * **Concept**: A list with bullets, like a shopping list.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
50. **`<ol>`**
    * **Concept**: A list with numbers or letters, like steps.
    * **Key Parameters**:
      * `start`: Starting number (e.g., `start="3"`).
      * `type`: List style (e.g., `type="A"`).
      * `id`, `class`: For naming parts.
51. **`<li>`**
    * **Concept**: An item in a `<ul>` or `<ol>`.
    * **Key Parameters**:
      * `value`: Custom number for `<ol>` (e.g., `value="5"`).
      * `id`, `class`: For naming parts.
52. **`<dl>`**
    * **Concept**: A list of terms and meanings, like a dictionary.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
53. **`<dt>`**
    * **Concept**: A term in a `<dl>`, like a word.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
54. **`<dd>`**
    * **Concept**: The explanation of a `<dt>`, like a definition.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
55. **`<table>`**
    * **Concept**: A grid for data, like a spreadsheet.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
56. **`<tr>`**
    * **Concept**: A row in a table.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
57. **`<th>`**
    * **Concept**: A header cell in a table, like a column title.
    * **Key Parameters**:
      * `scope`: Defines scope (e.g., `scope="col"`).
      * `id`, `class`: For naming parts.
58. **`<td>`**
    * **Concept**: A regular cell in a table for data.
    * **Key Parameters**:
      * `colspan`: Spans columns (e.g., `colspan="2"`).
      * `rowspan`: Spans rows (e.g., `rowspan="2"`).
      * `id`, `class`: For naming parts.
59. **`<thead>`**
    * **Concept**: The header part of a table.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
60. **`<tbody>`**
    * **Concept**: The main data part of a table.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
61. **`<tfoot>`**
    * **Concept**: The footer part of a table, like totals.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
62. **`<caption>`**
    * **Concept**: A title for a table.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.

**Example for Lists and Tables**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Lists and Tables</title>
  </head>
  <body>
    <ul>
      <li>Read stories</li>
      <li>Write comments</li>
    </ul>
    <ol start="3" type="A">
      <li value="5">Step 5</li>
      <li>Step 6</li>
    </ol>
    <dl>
      <dt>Story</dt>
      <dd>A fun tale</dd>
      <dt>Comment</dt>
      <dd>Your thoughts</dd>
    </dl>
    <table>
      <caption>Story Stats</caption>
      <thead>
        <tr>
          <th scope="col">Title</th>
          <th scope="col">Views</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Story 1</td>
          <td>50</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td colspan="2">Total: 50</td>
        </tr>
      </tfoot>
    </table>
  </body>
</html>
```

***

### 5. Media Tags

These tags add images, audio, video, or other media.

63. **`<img>`**
    * **Concept**: Shows a picture, like a photo.
    * **Key Parameters**:
      * `src`: Image file (e.g., `src="pic.jpg"`).
      * `alt`: Description for accessibility.
      * `width`, `height`: Size in pixels.
      * `loading`: Load style (e.g., `loading="lazy"`).
64. **`<audio>`**
    * **Concept**: Plays sound or music, like a music player.
    * **Key Parameters**:
      * `controls`: Shows play/pause buttons.
      * `src`: Audio file.
      * `autoplay`, `loop`: Auto-play or repeat.
65. **`<video>`**
    * **Concept**: Plays a video, like a movie player.
    * **Key Parameters**:
      * `controls`: Shows play/pause buttons.
      * `src`: Video file.
      * `poster`: Thumbnail image.
      * `autoplay`, `loop`: Auto-play or repeat.
66. **`<source>`**
    * **Concept**: Gives a file for `<audio>` or `<video>`.
    * **Key Parameters**:
      * `src`: File path.
      * `type`: File type (e.g., `type="video/mp4"`).
      * `media`: For specific devices (e.g., `media="(min-width: 600px)"`).
67. **`<track>`**
    * **Concept**: Adds subtitles or captions to `<video>` or `<audio>`.
    * **Key Parameters**:
      * `src`: Subtitle file.
      * `kind`: Type (e.g., `kind="subtitles"`).
      * `srclang`: Language (e.g., `srclang="en"`).
      * `label`: Subtitle name.
68. **`<picture>`**
    * **Concept**: Shows different images for different screens, like phones or PCs.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
69. **`<iframe>`**
    * **Concept**: Shows another webpage inside yours, like a video player.
    * **Key Parameters**:
      * `src`: Content URL.
      * `title`: Accessibility description.
      * `width`, `height`: Size in pixels.
70. **`<canvas>`**
    * **Concept**: Draws pictures or animations with code, like a digital canvas.
    * **Key Parameters**:
      * `id`: For code access.
      * `width`, `height`: Size in pixels.
71. **`<svg>`**
    * **Concept**: Draws shapes that don’t blur when zoomed, like a logo.
    * **Key Parameters**:
      * `width`, `height`: Size in pixels.
      * `viewBox`: Defines drawing area.

**Example for Media Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Media Page</title>
  </head>
  <body>
    <img src="photo.jpg" alt="Nature photo" width="200" loading="lazy">
    <audio controls>
      <source src="music.mp3" type="audio/mpeg">
      <track src="captions.vtt" kind="captions" srclang="en" label="English">
    </audio>
    <video controls poster="thumbnail.jpg" width="300">
      <source src="video.mp4" type="video/mp4">
      <track src="subtitles.vtt" kind="subtitles" srclang="es" label="Spanish">
    </video>
    <picture>
      <source srcset="small.jpg" media="(max-width: 600px)">
      <img src="large.jpg" alt="Responsive image">
    </picture>
    <iframe src="https://example.com" title="Embedded page" width="300" height="200"></iframe>
    <canvas id="myCanvas" width="100" height="100"></canvas>
    <script>
      const ctx = document.getElementById('myCanvas').getContext('2d');
      ctx.fillRect(10, 10, 50, 50);
    </script>
    <svg width="100" height="100">
      <circle cx="50" cy="50" r="40" fill="blue"></circle>
    </svg>
  </body>
</html>
```

***

### 6. Form Tags

These tags create forms for users to enter information.

72. **`<form>`**
    * **Concept**: A place to collect user info, like a survey.
    * **Key Parameters**:
      * `action`: Where data goes (e.g., `action="/submit"`).
      * `method`: How data is sent (e.g., `method="POST"`).
      * `aria-label`: Accessibility description.
73. **`<input>`**
    * **Concept**: A field for users to type or choose, like a text box.
    * **Key Parameters**:
      * `type`: Field type (e.g., `type="text"`, `type="email"`).
      * `name`: Field name.
      * `required`: Must be filled.
      * `value`: Default value.
74. **`<textarea>`**
    * **Concept**: A big box for typing lots of text.
    * **Key Parameters**:
      * `rows`, `cols`: Size of the box.
      * `name`: Field name.
      * `required`: Must be filled.
75. **`<button>`**
    * **Concept**: A clickable button, like “Send.”
    * **Key Parameters**:
      * `type`: Button type (e.g., `type="submit"`, `type="button"`).
      * `disabled`: Makes it unclickable.
76. **`<select>`**
    * **Concept**: A dropdown menu for picking options.
    * **Key Parameters**:
      * `name`: Field name.
      * `multiple`: Allows multiple choices.
77. **`<option>`**
    * **Concept**: An item in a `<select>` menu.
    * **Key Parameters**:
      * `value`: Data sent when chosen.
      * `selected`: Pre-selected option.
78. **`<optgroup>`**
    * **Concept**: Groups options in a `<select>` menu.
    * **Key Parameters**:
      * `label`: Group name.
      * `disabled`: Makes group unselectable.
79. **`<label>`**
    * **Concept**: Labels an input, like “Name:” for a text box.
    * **Key Parameters**:
      * `for`: Links to input’s `id`.
      * `id`, `class`: For naming parts.
80. **`<fieldset>`**
    * **Concept**: Groups form fields together, like a box around questions.
    * **Key Parameters**:
      * `disabled`: Disables all fields inside.
      * `id`, `class`: For naming parts.
81. **`<legend>`**
    * **Concept**: A title for a `<fieldset>`.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
82. **`<datalist>`**
    * **Concept**: Suggests options for an `<input>`, like autocomplete.
    * **Key Parameters**:
      * `id`: Links to `<input>`’s `list` attribute.
83. **`<output>`**
    * **Concept**: Shows the result of a form, like a calculation.
    * **Key Parameters**:
      * `for`: Links to input IDs.
      * `id`, `class`: For naming parts.
84. **`<progress>`**
    * **Concept**: Shows a progress bar, like for a task.
    * **Key Parameters**:
      * `value`: Current progress.
      * `max`: Total progress.
85. **`<meter>`**
    * **Concept**: Shows a gauge, like a score.
    * **Key Parameters**:
      * `value`: Current value.
      * `min`, `max`: Range.
      * `low`, `high`, `optimum`: Thresholds.

**Example for Form Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Contact Form</title>
  </head>
  <body>
    <form action="/submit" method="POST" aria-label="Contact form">
      <fieldset>
        <legend>Contact Us</legend>
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
        <label for="message">Message:</label>
        <textarea id="message" name="message" rows="4" cols="50"></textarea>
        <label for="topic">Topic:</label>
        <select id="topic" name="topic">
          <optgroup label="Categories">
            <option value="feedback" selected>Feedback</option>
            <option value="question">Question</option>
          </optgroup>
        </select>
        <label for="suggestion">Suggestion:</label>
        <input list="ideas" id="suggestion" name="suggestion">
        <datalist id="ideas">
          <option value="Story">
          <option value="News">
        </datalist>
        <label for="progress">Form Progress:</label>
        <progress id="progress" value="50" max="100"></progress>
        <label for="meter">Rating:</label>
        <meter id="meter" value="0.8" min="0" max="1"></meter>
        <output for="topic">Your topic: Feedback</output>
        <button type="submit">Send</button>
      </fieldset>
    </form>
  </body>
</html>
```

***

### 7. Other Tags

These tags handle special or miscellaneous content.

86. **`<div>`**
    * **Concept**: A general box for grouping things.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
87. **`<template>`**
    * **Concept**: Holds hidden content for later use, like a secret stash.
    * **Key Parameters**:
      * `id`: For code access.
88. **`<slot>`**
    * **Concept**: A placeholder for custom content in special components.
    * **Key Parameters**:
      * `name`: Identifies the slot.
      * `id`, `class`: For naming parts.
89. **`<data>`**
    * **Concept**: Links text to a value for computers.
    * **Key Parameters**:
      * `value`: Machine-readable data.
      * `id`, `class`: For naming parts.
90. **`<bdi>`**
    * **Concept**: Isolates text for different languages, like Arabic.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
91. **`<bdo>`**
    * **Concept**: Forces text direction, like right-to-left.
    * **Key Parameters**:
      * `dir`: Direction (e.g., `dir="rtl"`).
      * `id`, `class`: For naming parts.
92. **`<wbr>`**
    * **Concept**: Suggests where to break a long word.
    * **Key Parameters**: None.
93. **`<br>`**
    * **Concept**: Adds a line break, like pressing Enter.
    * **Key Parameters**: None.
94. **`<hr>`**
    * **Concept**: Draws a horizontal line to separate content.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
95. **`<address>`**
    * **Concept**: Shows contact info, like an email.
    * **Key Parameters**:
      * `id`, `class`: For naming parts.
96. **`<area>`**
    * **Concept**: Makes part of an image clickable, like a map.
    * **Key Parameters**:
      * `shape`: Shape (e.g., `shape="rect"`).
      * `coords`: Position (e.g., `coords="0,0,50,50"`).
      * `href`: Link URL.
      * `alt`: Accessibility description.
97. **`<map>`**
    * **Concept**: Groups clickable areas for an image.
    * **Key Parameters**:
      * `name`: Links to `usemap` attribute.
      * `id`, `class`: For naming parts.

**Example for Other Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Extras Page</title>
  </head>
  <body>
    <div class="container">
      <p>Contact: <address>info@example.com</address></p>
      <p>Line 1<br>Line 2</p>
      <hr>
      <p>Story <data value="123">Number 123</data></p>
      <p>Text in <bdi>العربية</bdi> and <bdo dir="rtl">English</bdo></p>
      <p>Superlongword<wbr>break</p>
      <img src="map.jpg" alt="Map" usemap="#mymap">
      <map name="mymap">
        <area shape="rect" coords="0,0,50,50" href="/story" alt="Story link">
      </map>
      <template id="hidden">
        <p>Hidden content</p>
      </template>
      <my-component>
        <slot name="content">Custom content</slot>
      </my-component>
    </div>
  </body>
</html>
```

***

### 8. Deprecated or Rarely Used Tags

These tags are old or not recommended but part of HTML5 for completeness.

98. **`<acronym>`**
    * **Concept**: Old tag for abbreviations (use `<abbr>` instead).
    * **Key Parameters**:
      * `title`: Full term.
      * `id`, `class`: For naming parts.
99. **`<applet>`**
    * **Concept**: Old tag for Java applets (not used anymore).
    * **Key Parameters**:
      * `code`: Java file.
      * `width`, `height`: Size.
100. **`<basefont>`**
     * **Concept**: Old tag to set default font (not used now).
     * **Key Parameters**:
       * `size`, `color`, `face`: Font settings.
101. **`<big>`**
     * **Concept**: Old tag to make text bigger (not used now).
     * **Key Parameters**:
       * `id`, `class`: For naming parts.
102. **`<center>`**
     * **Concept**: Old tag to center content (not used now).
     * **Key Parameters**:
       * `id`, `class`: For naming parts.
103. **`<font>`**
     * **Concept**: Old tag to style text (not used now).
     * **Key Parameters**:
       * `size`, `color`, `face`: Font settings.
104. **`<strike>`**
     * **Concept**: Old tag to cross out text (use `<del>` instead).
     * **Key Parameters**:
       * `id`, `class`: For naming parts.
105. **`<tt>`**
     * **Concept**: Old tag for typewriter text (use `<code>` instead).
     * **Key Parameters**:
       * `id`, `class`: For naming parts.

**Example for Deprecated or Rarely Used Tags**:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Old Tags Page</title>
  </head>
  <body>
    <p><acronym title="World Wide Web">WWW</acronym> is old.</p>
    <p><applet code="game.class" width="100" height="100"></applet></p>
    <p><basefont size="4" color="blue" face="Arial">Text</basefont></p>
    <p><big>Big text</big></p>
    <center>Centered content</center>
    <p><font size="3" color="red">Red text</font></p>
    <p><strike>Crossed out</strike></p>
    <p><tt>Typewriter text</tt></p>
  </body>
</html>
```

***

### Notes

* Each example is a complete HTML file you can test in a browser.
* The examples are simple and beginner-friendly, focusing on HTML structure.
* Avoid deprecated tags (like `<font>`) in real projects; they’re included for completeness.
* If you want to add styles (CSS), interactivity (JavaScript), or learn how to use these in a bigger project, let me know!
