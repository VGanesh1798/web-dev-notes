# HTML Basics
HTML stands for **H**yper**t**ext **M**arkup **L**anguage. It is not a programming language but is instead a markup language that tells the browser how to display text and other elements. HTML can be thought of as the "skeleton" of a website.

## Basic Elements and Attributes
Most elements in HTML have opening and closing tags, like `<p>` and `</p>` for example. The content goes in between these tags. Other elements are empty, like the `<img>` tag.

Elements can further be distinguished between block elements and inline elements. Block elements like `<p>` create new blocks of content, while inline elements like `<a>` follow the lines on the page and wrap around.

Elements often have attributes like a class, ID, or a title. Some attributes like `href` are particularly important because they help the element function properly. Some attributes like `disabled` are boolean and do not need to have values assigned to them.

## Anatomy of HTML
An `index.html` file serves as the entry point for the browser to connect to other files. All HTML files begin with `<!DOCTYPE html>` at the start, and the rest of the content is wrapped in `<html>` tags.

The two main sections of content are in `<head>` and `<body>`. The header contains valuable information like the page's title in a `<title>` element, metadata in `<meta>` tags, and links to CSS, favicons, or other files in `<link>` tags. The body contains everything that will be rendered on the page itself.

An important piece of metadata is to define the character set. The most common character set is UTF-8, so we use `<meta charset="utf-8">`. Note that setting the character set is different from setting the language. To set the language to something like American English, add `lang="en-US"` to the HTML tag. In the body, subsections of a language can be specified too: `<span lang="ja">` specifies that a portion of the text is in Japanese instead of English. 

Metadata is incredibly useful for search engine optimization (SEO). Other than the character set, we can define the author, page description, and more to make a website easily searchable by Google.

Some characters are reserved in HTML, like the double and single quote characters. In order to display these characters, entity references like `&quot;` or `&apos;` will have to be used. All entity references begin with an ampersand and end with a semicolon.

Finally, to leave comments, begin with `<!--` and end with `-->`.

## Text Basics
There are 6 levels of headings in HTML, ranging from `<h1>` to `<h6>`. These headings are also **semantic**, meaning that they define very particular elements. Other semantic text elements include `<em>` for *italics* and `<strong>` for **bold**. These semantic tags replaced the old `<i>` and `<b>` tags because they are more useful for screen-readers to read the text to people who cannot see. The semantic tags tell the screen reader how to read the text (by changing tone of voice, for example). Of course there's still a place for the old tags, like when semantics aren't needed. The `<u>` tag should still probably not ever be used since underlines are too often confused with links.

`<p>` tags are used for paragraphs of text. They are not semantic in any way, and neither are `<span>` tags (an inline text element). We can of course style these elements to *look* like semantic elements, but it won't benefit us.

Lists can be ordered with `<ol>` or unordered with `<ul>`. All list elements are wrapped in `<li>` tags. Lists can also be nested.

## Hyperlinks
The `<a>` tag is for hyperlinks and requires the `href` attribute to assign a URL to redirect to. A `title` attribute is also helpful for mouseover information. Since elements can be nested, we can turn any element, even an image, into a hyperlink.

We can even link to other fragments in an html document if we include a hash symbol, followed by the element `id` after the URL to a file. To link to part of the same document, we can just omit the `blah.html` part of this statement and link directly to the element with `#coolid`.

Links can be absolute, meaning that they contain information all the way up to the HTTP protocol. They can also be relative, meaning that they contain information that is relative to the location of the `index.html` file. It is often best to use relative links when we are only linking to our own files.

Finally, we can even add an email hyperlink by setting href to something like `mailto:me@cool.com`. This email link can also contain information like the subject, cc, etc.

## Advanced Text
Descriptive lists are denoted by `<dl>` and are used for things like definitions. Each item has a title in `<dt>` and a description in `<dd>`.

Quotes are often presented in blocks using `<blockquote>`, but inline quotes can be made using `<q>`. These elements have a `cite` attribute to cite where the quote came from. Citations themselves can be added using `<cite>` tags.

Abbreviations can have full descriptions appear when the text is hovered over. Use `<abbr>` with a `title` attribute to describe the text being abbreviated.

Another semantic element is the `<address>` element, which wraps other text in something like `<p>` to denote it as being an address.

Superscript and subscript are made using `<sup>` and `<sub>`. Computer code is often wrapped by `<code>` tags, and whitespace is made using `<pre>`. Variable names can be wrapped in `<var>`, keyboard inputs in `<kbr>`, and program outputs in `<samp>`, though all look the same as `<code>`.

Time can be denoted using `<time>` tags with a `datetime` attribute. Set this equal to any of a variety of date/time formats.

## Document Sections
Semantic tags also exist for structuring HTML documents. These elements wrap around textual elements in order to group them by purpose. `<header>` is used to denote a document's header, usually at the top of a page. `<nav>` is used to denote a navigation bar. `<main>` wraps content *unique to a page*. The `<section>` and `<article>` elements are useful to group content by purpose, and `<aside>` can be used for sidebars (though they won't appear on the side without CSS). Lastly, `<footer>` is used for, well, the footer. All of these elements can be nested in different areas too, for example if a large section of the document has its own header. The only element that should not be reused is `<main>`.

Non-semantic structural tags include `<div>` for blocks and `<span>` for inline. The `<div>` tag is very useful, but don't overuse it.

Line breaks are accomplished by using `<br>`, and a horizontal rule can be placed with `<hr>`.