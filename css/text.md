# CSS Text
In CSS, text can be styled to your liking. You can make a span look like a header, or make a header look like a subscript. 

## Text and Font Styling
Text is an inline element that flows along the page until the end of line is reached or a line break is put in with `<br>`. Text can either be styled by changing font or layout.

Text color is changed using `color`, and `font-family` changes the look of the text. Fonts can be `serif`, `sans-serif`, `monospace`, `cursive` and `fantasy`. Using a **font stack** allows us to choose multiple fonts for a browser to pick from, in case it doesn't support one (looking at you, Internet Explorer).

Font size is changed using `font-size` accordingly and can have units like `px` and `em`. `font-style` can affect *italic* text, and `font-weight` can affect **bold** text. `text-decoration` affects <u>underlined</u> text, and `text-transform` can affect CAPITALIZATION. To add shadows to text, use `text-shadow`.

Text layout is the second method of styling, and involves properties like `text-align` and `line-height`. Spacing can be changed using `letter-spacing` and `word-spacing`. There are lots of other properties worth checking out, but I won't list them here.

The shorthand property `font` combines many of the different properties that can be applied to fonts. Only a `font-size` and `font-family` are required for it to be valid. 

## Styling Lists
Lists have some special styling properties and practices to consider. Among these is changing the horizontal and vertical spacing of lists.

Some list specific properties include `list-style-type` for changing the bullets/numbering and `list-style-position` to change where the bullets/numbers go. `list-style-image` allows us to use an image instead of a bullet. The shorthand `list-style` can be used to combine all of these into one rule.

HTML itself has some cool list styling. The `start` attribute can set a new start number, and `reversed` makes the list count down. Each `<li>` can have its own `value` to set a different number for each one too. CSS counters are a more advanced way of styling list numbering.

## Styling Links
Links have some default styling placed on them, like coloring and an underline, and they benefit from pseudoclasses like `:hover`. When making custom list styling, the order of the rules matters. Use the mnemonic **L**o**V**e **F**ears **HA**te to remember the order of pseudoclasses after the basic selector: `:link`, `:visited`, `:focus`, `:hover`, and `:active`. Attribute selectors can let us add icons to links.

Custom link styling is useful when making links to look like buttons for a navbar.

## Web Fonts
Unfortunately, `font-family` is limited to only Web-safe fonts, which can get boring. CSS offers an alternative called Web fonts, which allow us to download new fonts from online. To add them, place a `@font-face` block at the start of a .css file and include the properties `font-family` to name the new font and `src` to specify from where to download the font. Now, this new font can be used with `font-family` in the future.