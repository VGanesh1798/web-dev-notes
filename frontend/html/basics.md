# HTML Basics
HTML stands for **H**yper**t**ext **M**arkup **L**anguage. It is not a programming language but is instead a markup language that tells the browser how to display text and other elements. HTML can be thought of as the "skeleton" of a website.

## Sample Anatomy
An HTML document can look like the following:
```
<!DOCTYPE html>
<html lang="en-US">
    <head>
        <meta charset="utf-8">
        <title>My Document</title>
        <link rel="shortcut icon" href="favicon.ico type="image/x-icon>
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
