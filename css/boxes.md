# CSS Boxes

## Box Model Recap
Box height and width can be constrained by setting max/min values for both. Keep in mind that box heights don't support percentages and need units like `px` or `em`. Using `margin: 0 auto` sets the top/bottom margins to zero while centering the content by sharing space between the left/right margins.

The total width of a box is the sum of its `width`, `padding-right`, `padding-left`, `border-left`, and `border-right`. To tweak the box model entirely, use the `box-sizing` property. The value `border-box` is useful for this property.

In addition to the block and inline box types, some others include `flex`, `table`, and `grid`. These will be discussed in future notes.

## Backgrounds
Background colors and images have already been explained, but `background-repeat` is a special property used to specify how the background image will repeat. To change the (x, y) position of the image within the background, use `background-position`. `background-size` changes the size of the image in the background; it is useful when putting icons in links.

The `background-image` can take `linear-gradient()` as a value instead of an image. This function specifies the gradient direction and the two colors it ranges between. Other parameters include color-stops, which are other defined color points between the two bounds.

Background scrolling behavior is controlled via `background-attachment`. It can take three values of `scroll`, `fixed`, and `local`.

The `background` shorthand combines many of these longhand properties. Lastly, it is possible to specify multiple backgrounds that will then stack on top of one another on the page.

## Borders
Borders have a size of 0 by default, which makes them invisible. The `border` shorthand allows us to set the thickness, style, and color all at once. Each side of the border can also be styled separately.

Rounded borders are in style now, and we use `border-radius` to set their size. Each corner can be specified separately too. To make elliptical borders, separate the radii values by a forward slash.

Images can also be used in the border, via the `border-image` property. Always use `border` in conjunction with `border-image` as a fallback. Images are divided into a 9-cell grid when being converted into a border (the center cell is not part of the border though). These grids are created with `background-clip: padding box` and an image can be specified in `background-image-source` with the `url()` function. Other properties set the corner sizes, repeats, and more.

## Styling Tables
Tables greatly benefit from the rule `table-layout: fixed` which makes them behave more predictably. Additionally, the pseudoclass `:nth-child()` is very useful when trying to style rows separately. The `border-collapse: collapse` rule gets rid of the extra lines between cell borders by collapsing them all into one border. Lastly, a `border` and `padding` can help add some space in the table and keep things from being cramped.

Additional styling tips include using zebra-striped rows for better readability, and using `text-align` to line up cells.

## Advanced Box Effects
Much like `text-shadow`, CSS has `box-shadow` which can be used to specify multiple box shadows too. One difference is that `box-shadow` has an `inset` keyword to make an inner shadow rather than an outer shadow.

Filters in CSS are a more recent feature that work kind of like Photoshop filters. They're used with the `filter` property and any of several functions. Often, a `-webkit-` prefix will be added to filters; this is called a vendor prefix and is required for Chrome, Opera, and Safari, but not for Firefox or Edge.

Blend modes specify how different elements blend together when they overlap, and two properties that are used for blend modes are `background-blend-mode` and `mixed-blend-mode`. The former blends multiple background images and colors set on a single element, while the latter blends together the element it is set on with overlapping elements.

The `background-clip` property has a value `text` which when paired with the rule `-webkit-text-fill-color: transparent` allows us to clip background images to the shape of an element's text, creating some cool effects. It's not an official standard but is becoming more widely used.
