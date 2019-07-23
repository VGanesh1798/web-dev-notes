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
HTML5 added some native media support, so there is pretty much no need for Flash or other buggy plugins.

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
Forms are defined using the `<form>` attribute and have `action` and `method` to define the URL to send data to via an HTTP method. The two most common methods are GET and POST. Using developer tools, we can track GET and POST requests and see headers such as `Host`, `Content-Length`, and `Content-Type`. The server-side language can receive and use this data in many different ways, and multiple frameworks exist to aid in these tasks.

When sending files, the POST method must be used and additionally, the `enctype` attribute for the form must be set to `multipart/form-data`. This changes the `Content-Type` header from the default value of `application/x-www-form-urlencoded`. The new value tells the browser that data has been split into multiple parts.

Modern HTML forms typically use Javascript to send the data rather than HTML itself. Data is typically sent asynchronously to only update the parts of the page that need to be updated. This method is called AJAX, with the 'X' standing for XML (although JSON is used much more now). `XMLHttpRequest` can be used manually in Javascript to send data, and the `FormData` object assists in making this simpler. `FormData` can be bound to a `<form>` element.

Another (bad) way to send form data is to build a form using the DOM API, putting the data in an `<iframe>`, and then retrieving the content from the iframe. It's a risky method for sure. When sending files, the `FileReader` API comes into use.

### Form Structure
```
<input>      # Default inline input
name         # Input name, used for submission
type         # Input type
id           # Input ID for reference with labels
value        # Used to set a value for an input
disabled     # Attribute used to disable an input
autofocus    # Attribute used to set focus on input
form         # Attribute used to link external widgets to a form; not actually supported

<textarea>   # Text box input

<button>     # Button
type         # Button type

<style>      # Used to write CSS directly into HTML

<fieldset>   # Groups widgets that share common functions and properties
<legend>     # Label for <fiedset> that goes right below opening tag
<label>      # Label for inputs
for          # Label attribute that references input ID
```

### Input Types
```
<button>         # Button widget 
submit           # Submit form
reset            # Reset form
button           # Does nothing but is useful for custom functionality

<input>          # Most common input widget
text             # Default type for inputs
checkbox         # Checkboxes
radio            # Radio buttons
button           # Redundant button input
number           # Number input
range            # Sliding number input
datetime-local   # For date and time
month            # Month input
time             # Time input
week             # Week input
color            # Color input via hex codes
file             # For inputting files
hidden           # Hides input; requires name and value
image            # Image input


<select>         # Dropdown menu
multiple         # Attribute to allow multiple choice menu
<option>         # Options in dropdown menu
selected         # Attribute to mark option as preselected
<datalist>       # Autocomplete menu
list             # Attribute used to link input to datalist via datalist's ID

<progress>       # Progress bar that can have a max value
<meter>          # Optimality meter
```
Checkboxes only send their data if they are checked; this contrasts with other inputs, which send data no matter what. Usually, checkboxes are placed as items of a list inside of a `<fieldset>` element with a corresponding `<legend>`. An additional attribute is the `checked` attribute. Radio buttons with the same `name` are grouped together, and only one of the buttons can be selected at a time. The `value` of this button is then sent, and if no buttons are selected, no value is sent at all.

The `number` and `range` inputs can (and should, for the slider) have `min`, `max`, and `step` defined. Sliders don't actually provide any visual indicator of what the selected value is; this has to be implemented using a `<span>` element and some Javascript. Time/date inputs can also be constrained using `min` and `max`. Meters are limited by `min` and `max`. They also take a `low` and `high`, as well as an `optimum`, to divide up the range of values and color the meter either red, yellow, or green depending on how optimal the current value is.

The types of files to pick can be constrained using the `accept` attribute, and `multiple` can be used too.

Inputs set to `image` will inherit all of the same attributes as `<img>`. These image buttons can be used to submit forms and send two key/value pairs. The keys consist of the `name` followed by the x and y coordinates of the click.

We can combine HTML with CSS and Javascript to make our own form widgets. Javascript is unreliable technology however, so be wary of doing this. The DOM API is useful when adding functionality, but for browsers that have issues (like IE), libraries like jQuery are useful. To make widgets accessible, we can use the `role` and `aria-selected` attributes.

### Form Validation
Although data should be validated on the server-side, the client-side does offer some form validation. A valid form input matches the `:valid` CSS pseudoclass and can be styled accordingly; its data will be sent upon submission, unless Javascript blocks this function. In contrast, invalid form inputs match the `:invalid` pseudoclass and submission will fail until the input becomes valid. The error message that appears can be changed using Javascript, by the way.

The `required` attribute is the simplest method of input validation. Another useful validator is the `pattern` attribute, which matches the input to a specified regular expression. The `minlegnth` and `maxlength` attributes can be used on text inputs much like `min` and `max` are used for numerical inputs.

Javascript is also used to validate forms on the client-side. The constraint validation API is useful in this regard, but the validation can be done without it (although this is much harder).