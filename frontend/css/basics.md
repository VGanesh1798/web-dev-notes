# CSS Basics
CSS stands for **C**ascading **S**tyle **S**heets. It is not a programming language but is instead a styling language that affects markup languages like HTML to change the look and feel of elements. Combined with HTML, CSS forms the Document Object Model, also called the DOM. CSS can be thought of as the "clothing" of a website.

## Anatomy
- Properties and values pair together to form declarations
- Declarations are applied to selectors to form rules
- Rules are a kind of statement
- At-rules are statements that tell CSS how to behave
- Comments are formed like `/* COMMENT */`

## Selectors
```
ELEMENT                   # Select element
.CLASS                    # Select elements based on class
#ID                       # Select elements based on ID
*                         # Universal selector

[ATTR=VAL]                # Value of ATTR is VAL
[ATTR~=VAL]               # ATTR contains VAL in a list of values
[ATTR^=VAL]               # Value of ATTR begins with VAL
[ATTR$=VAL]               # Value of ATTR ends in VAL
[ATTR*=VAL]               # Match VAL substring in ATTR

SELECTOR:PSEUDOCLASS      # Style element based on a special state
SELECTOR::PSEUDOELEMENT   # Style specific parts of element

A B                       # Descendent combinator
A > B                     # Direct child combinator
A + B                     # Adjacent sibling combinator
A ~ B                     # General sibling combinator

A, B                      # Group multiple selectors
```

## Values and Units
- Numeric units can be either absolute or relative
  - `px` is an absolute unit of measurement
  - `em` is a relative unit of measurement
    - `1em` defaults to `16px`
    - `rem` is a more useful version of `em` since it overrides inherited font sizes
- The value `0` can be unitless
- The `line-height` property can take unitless values to act as a multiplier
- Colors can be expressed using names, hex codes, or functions like `rgb()` and `hsl()`
  - To change opacity, use the `opacity` property or the functions `rgba()` and `hsla()`.

Percentages are useful when trying to resize things based on the size of the parent element. Layouts using percentages can be called **liquid layouts** because the layout changes as the viewport changes; the opposite layout is a **fixed-width layout**.

## Cascade and Inheritance
What does "Cascade" even mean? Essentially, the Cascade controls what rules are inherited from parent elements, and at a basic level this means that the order of rules matters. At a more detailed level, this means that selectors win out based on importance, specificity, and source order, in decreasing order of weight.
- Rules can be overriden using `!important`
- More specific selectors override less specific ones; ID selectors are most specific
- Later properties override older ones for the same selector

Inheritance can be controlled with four values:
- `inherit` makes child always inherit property value
- `initial` makes child use browser's default stylesheet for that property value
- `unset` reverts property back to natural value
- `revert` reverts property back to value it would have had before additional styling
- `all` shorthand can apply one of these settings to almost all properties at once

## Box Model
CSS styling adheres to the box model, where each element is represented as a box stacked on top of other boxes. These boxes of `length` and `width` have multiple layers around them, consisting of `padding`, `border`, and `margin`. 

Using absolute units can sometimes cause box content to spill out and overflow. To control this behavior, use the `overflow` property.

Background images and colors naturally extend to the outer edge of the box border, which can be annoying sometimes. To change this, use the `background-clip` property to control how far the background extends.

Boxes also have an `outline`, which is not part of the box model but is often used for accessibility reasons to highlight active items.

Lastly, boxes have a `display` that affects how they stack. `block` elements stack on top of one another and `inline` elements wrap around the page, flowing with text. A third type is `inline-block`, which sort of combines the flowing nature of inline boxes but can have its height and width affected like block boxes.

## Text
Text is an inline element that flows along the page until the end of line is reached or a line break is put in with `<br>`. Text can either be styled by changing font or layout. Using a **font stack** allows us to choose multiple fonts for a browser to pick from, in case it doesn't support one (looking at you, Internet Explorer).

### Font Styling
```
font              # Shorthand that combines many of the properties below

font-family       # Specify a font and font style; required for shorthand
serif             # Serif font style
sans-serif        # Sans-serif font style
monospace         # Monospace font style
cursive           # Cursive font style
fantasy           # Fantasy font style

font-size         # Affects font size; required for shorthand
font-style        # Affects italic text
font-weight       # Affects bold text
text-decoration   # Affects underlined text
text-transform    # Affects capitalization
text-shadow       # Affects text shadowing
color             # Changes text color

text-align        # Align text on page
line-height       # Change size of lines
letter-spacing    # Change space between letters
word-spacing      # Change space between words
```

### List Styling
- A list's horizontal and vertical spacing is often what should be styled
- The `list-style` shorthand combines the following properties:
  - `list-style-type` changes the bullet or numbering style
  - `list-style-position` changes where the bullets or numbers go
  - list-style-image` allows us to use an image instead of a bullet

HTML itself has some cool list styling. The `start` attribute can set a new start number, and `reversed` makes the list count down. Each `<li>` can have its own `value` to set a different number for each one too. CSS counters are a more advanced way of styling list numbering.

### Link Styling
Links have some default styling placed on them, like coloring and an underline, and they benefit from pseudoclasses like `:hover`. When making custom list styling, the order of the rules matters. Use the mnemonic **L**o**V**e **F**ears **HA**te to remember the order of pseudoclasses after the basic selector: `:link`, `:visited`, `:focus`, `:hover`, and `:active`. Attribute selectors can let us add icons to links.

### Web Fonts
Unfortunately, `font-family` is limited to only Web-safe fonts, which can get boring. CSS offers an alternative called Web fonts, which allow us to download new fonts from online. To add them, place a `@font-face` block at the start of a .css file and include the properties `font-family` to name the new font and `src` to specify from where to download the font. Now, this new font can be used with `font-family` in the future.

## Boxes
Box height and width can be constrained by setting max/min values for both. Keep in mind that box heights don't support percentages and need units like `px` or `em`. Using `margin: 0 auto` sets the top/bottom margins to zero while centering the content by sharing space between the left/right margins.

The total width of a box is the sum of its `width`, `padding-right`, `padding-left`, `border-left`, and `border-right`. To tweak the box model entirely, use the `box-sizing` property. The value `border-box` is useful for this property.

In addition to the block and inline box types, some others include `flex`, `table`, and `grid`. These will be discussed in future notes.

### Backgrounds
Background colors and images have already been explained, but `background-repeat` is a special property used to specify how the background image will repeat. To change the (x, y) position of the image within the background, use `background-position`. `background-size` changes the size of the image in the background; it is useful when putting icons in links.

The `background-image` can take `linear-gradient()` as a value instead of an image. This function specifies the gradient direction and the two colors it ranges between. Other parameters include color-stops, which are other defined color points between the two bounds.

Background scrolling behavior is controlled via `background-attachment`. It can take three values of `scroll`, `fixed`, and `local`.

The `background` shorthand combines many of these longhand properties. Lastly, it is possible to specify multiple backgrounds that will then stack on top of one another on the page.

### Borders
Borders have a size of 0 by default, which makes them invisible. The `border` shorthand allows us to set the thickness, style, and color all at once. Each side of the border can also be styled separately.

Rounded borders are in style now, and we use `border-radius` to set their size. Each corner can be specified separately too. To make elliptical borders, separate the radii values by a forward slash.

Images can also be used in the border, via the `border-image` property. Always use `border` in conjunction with `border-image` as a fallback. Images are divided into a 9-cell grid when being converted into a border (the center cell is not part of the border though). These grids are created with `background-clip: padding box` and an image can be specified in `background-image-source` with the `url()` function. Other properties set the corner sizes, repeats, and more.

### Styling Tables
Tables greatly benefit from the rule `table-layout: fixed` which makes them behave more predictably. Additionally, the pseudoclass `:nth-child()` is very useful when trying to style rows separately. The `border-collapse: collapse` rule gets rid of the extra lines between cell borders by collapsing them all into one border. Lastly, a `border` and `padding` can help add some space in the table and keep things from being cramped.

Additional styling tips include using zebra-striped rows for better readability, and using `text-align` to line up cells.

### Advanced Box Effects
Much like `text-shadow`, CSS has `box-shadow` which can be used to specify multiple box shadows too. One difference is that `box-shadow` has an `inset` keyword to make an inner shadow rather than an outer shadow.

Filters in CSS are a more recent feature that work kind of like Photoshop filters. They're used with the `filter` property and any of several functions. Often, a `-webkit-` prefix will be added to filters; this is called a vendor prefix and is required for Chrome, Opera, and Safari, but not for Firefox or Edge.

Blend modes specify how different elements blend together when they overlap, and two properties that are used for blend modes are `background-blend-mode` and `mixed-blend-mode`. The former blends multiple background images and colors set on a single element, while the latter blends together the element it is set on with overlapping elements.

The `background-clip` property has a value `text` which when paired with the rule `-webkit-text-fill-color: transparent` allows us to clip background images to the shape of an element's text, creating some cool effects. It's not an official standard but is becoming more widely used.