# HTML Basics
HTML stands for **H**yper**t**ext **M**arkup **L**anguage. It is not a programming language but is instead a markup language that tells the browser how to display text and other elements. HTML can be thought of as the "skeleton" of a website.

## Sample Anatomy
An HTML document can look like the following:
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>My Document</title>
        <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    </head>
    <body>
        <h1>Heading</h1>
        <p>Sample paragraph</p>
    </body>
</html>
```
Comments look like `<!-- COMMENT -->`.

## Entity References
```
&excl;    !
&quest;   ?
&num;     #
&amp;     &
&apos;    '
&quot;    "
&gt;      >
&lt;      <
```

## Metadata
All metadata goes in the header of the document.
- To specify a language, add the `lang` attribute to `<html>`
  - Other sections of the document can specify different languages with this attribute on a `<span>`.
- `<title>` specifies the page's title
- `<meta>` can be used to denote the character encoding, the author and description, and more
- `<link>` is used to add favicons, CSS, and other stuff to a document.
  - Use the `rel` attribute to denote what the object is and the `href` attribute to link to it.
- `<script>` is used to add Javascript with the `src` attribute and should typically go at the end of the body of the document, not the header.

## Text Elements
```
<h1> - <h6>   # Headings
<p>           # Paragraph

<ol>          # Ordered list
<ul>          # Unordered list
<li>          # List item

<em>          # Emphasis (semantic italics)
<i>           # Italics
<strong>      # Strong (semantic bold)
<b>           # Bold
<u>           # Underline
```

## Hyperlinks
Hyperlinks are made using the `<a>` tag and require the `href` attribute; a `title` is also helpful.

Link to fragments of an html document by including the element's `id` after the URL in the `href`. For the same document, omit the URL part and link directly to an element (for example, `href=#coolid`).

We can set email hyperlinks: for example, `href=mailto:me@cool.com`. The link can also contain subject info and CCs.

## Text Formatting
```
<dl>           # Descriptive list
<dt>           # Descriptive list item title
<dd>           # Descriptive list item description

<blockquote>   # Block element for quotes
<q>            # Inline element for quotes
cite           # Attribute for citing quotes
<cite>         # Citation

<abbr>         # Abbreviation
title          # Attribute to describe abbreviation

<address>      # Wraps around text to denote address

<sup>          # Superscript
<sub>          # Subscript

<code>         # Code block
<pre>          # Whitespace block
<var>          # Variable names
<kbr>          # Keyboard inputs
<samp>         # Program outputs

<time>         # Time
datetime       # Attribute for setting date and time
```

## Document Sections
```
<header>    # Semantic element to wrap header
<nav>       # Semantic element to wrap navigation bar
<main>      # Semantic element to wrap content unique to page
<section>   # Semantic element to wrap a section
<article>   # Semantic element to wrap an article
<aside>     # Semantic element to wrap a sidebar
<footer>    # Semantic element to wrap a footer

<div>       # Block element to wrap a section of content
<span>      # Inline element to wrap a section of content

<br>        # Line break
<hr>        # Horizontal rule
```

## Media
HTML5 added some native media support, so the need for Flash and other buggy plugins is effectively gone now.

### Images
- Insert images using `<img>` and specify the `src` and `alt`
  - A `title` is also useful
  - Images can be resized using `height` and `width`
- A `<figure>` wraps `<img>` and `<figcaption>`
- To specify multiple sources for an image, we can wrap `<source>` elements in a `<picture>` element
- The `srcset` and `sizes` attributes let the browser pick the best image to display from a list of sources

### Audio and Video
- Insert audio using `<audio>` and specify the `src`
  - To specify multiple sources, put all `src` attributes into a `<source>`
- Insert video using `<video>` and specify the `src` or `<source>`
  - To display fallback text, use `alt` like for `<img>`
  - Useful attribute include `controls`, `loop`, `muted`, and `autoplay`
  - Resize video with `height` and `width`
  - Subtitles can be added using `<track kind="subtitles">` and setting the `src` and `srclang` attributes. The subtitle file should be in .vtt format

### Embedded Content
- Use `<iframe>` to embed other Web documents
  - Replaces `<object>` and `<embed>`, which are for old and buggy plugins
  - Only use iframes with HTTPS and always specify `sandbox` attribute
- For Javascript-rendered images, use `<canvas>`

### Vector Graphics
Vector graphics are better for icons but worse for things like photographs. There are three ways to include vector graphics in HTML:
- Hardcode into document with `<svg>`
- Make in program like Inkscape and link with `<img>`
- Embed using `<iframe>`

## Tables
```
<table>      # Table wrapper
<td>         # Table data cell
<tr>         # Table row
<th>         # Table header that goes at start of a row

rowspan      # Attribute to change how many rows a cell spans
colspan      # Attribute to change how many columns a cell spans

<colgroup>   # Group columns for styling
<col>        # Column
span         # Attribute to apply same styling to multiple columns

<caption>    # Caption that goes at top of table

<thead>      # Table head
<tbody>      # Table body
<tfoot>      # Table footer
```
- Apply the `scope` attribute to `<th>` to describe what a row is for
  - Can set this to `rowgroup` or `colgroup` if it spans multiple rows/columns
- Attach `id` to `<th>` and `headers` to each cell in the header's group to create association

## Forms
Forms are defined using the `<form>` attribute and have `action` and `method` to define the URL to send data to via an HTTP method.
