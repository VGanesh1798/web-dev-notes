# CSS Layout

## Normal Flow
In the box model, elements have a content area of certain width and height which is directly surrounded by padding. This padding is bounded by a border, which is then surrounded by a margin. An outline exists somewhere inside the margin, but is not part of the box model itself.

A block element's content is 100% of the width of the parent container and as tall as the content allows. An inline element's content is both as wide and as tall as the content allows. This is why inline element's cannot have their height and width changed.

Normal flow is the way objects are naturally placed on the viewport. Block elements follow the block flow, while inline elements follow inline flow. Messing with the layout when styling will always go against the normal flow, so it is a good idea to first have a well-structured HTML body to work from when changing the layout up.

If two adjacent elements have their margins set and they touch, the larger margin wins out and the other one "collapses".

## Flexbox
The **Flexible Box Layout** is a newer layout that helps to alleviate layout limits that floats and positioning couldn't fix. It lays elements out in one direction, either a row or a column. To use it, add `display: flex` to the parent container, and all of its children elements will become flex items. Note that inline items can be flexed by using `inline-flex` instead.

Flex items have two axes: the main axis runs in the flex direction, and the cross axis runs in the perpendicular direction. Specifying `flex-direction` for the flex container can change the main axis to be either a row or column (the default is a row).

Oftentimes, flex items will overflow out of the container and ruin the model. To fix this, add `flex-wrap: wrap` to the container's styling. The shorthand `flex-flow` will combine the direction and wrap properties.

We will want to add `flex` properties to flex items, especially when wrapping. This property changes the sizing of different items in relation to the container. The value for `flex` can be unitless or have units of measurement.

`flex` itself is a shorthand for a number of other properties. `flex-grow` is the unitless property that affects how much available space along the main axis an item will take up. `flex-shrink` is more advanced, affecting how items shrink when they overflow the container. `flex-basis` is the property with units that affects the minimum size of flex items.

Flexbox features can be used to help align items along either axis, and flex items can be ordered (even with negative numbers!) by using `order`.

Lastly, flex items can themselves be flex containers, allowing for some interesting and complicated layouts to be formed.

## Grid
Grids are another CSS3 feature that are more useful for large layouts. Grids have rows and columns, along with gutters to separate the rows and columns. To use a grid, add `display: grid` to the parent element. Grids can be templated by using `grid-template-columns` or `grid-template-rows` to get sizes for as many columns as desired. Repeat notation allows us to repeat all or part of our grid layout. Use `repeat()` on the track listing property. We can also set grid gaps: the shorthand `grid-gap` accomplishes this for both rows and columns.

Grid columns/rows can be flexibly sized with the `fr` unit, with `1fr` representing one fraction of the space in a grid container. To make a certain row or column bigger, give it a higher fraction of the grid space. Gaps cannot have `fr` units.

We have defined the *explicit* grid above, but the *implicit* grid is formed outside of what we define. Assuming we only define one of rows or columns, the other direction is our implicit grid. We can resize the implicit grid from `auto` to something of our choice by using either `grid-auto-rows` or `grid-auto-columns` in the parent container. Since grid items can still overflow, it's a good idea to use `minmax()` as a value for this property. Setting the max value to `auto` lets the item resize itself as it needs to.

If we want the grid to make as many rows or columns as will fit, in the `repeat()` function use `auto-fill` as the number of repeats. We can then set the size to a `minmax()` function with `1fr` as the maximum to distribute remaining space evenly.

The shorthand properties `grid-column` and `grid-row` can be used to set the start and end columns for items in a grid. These two values are separated by a forward slash. This is called line-based positioning.

An alternative to the above is to use `grid-template-areas` to essentially write out a drawing of what items fill what spots in the grid. In each component, add a `grid-area` and give the value of the content name in the template.

## Floats
Once used to do layouts, the `float` property has returned to its original purpose of moving items around on the page. Since floats remove items from normal flow entirely, other elements will display beside floated items. To avoid this, add `cleared` properties to elements you do not want to sit next to floated elements.

With small paragraphs, a simple `cleared: left` or something isn't enough. We can use a "clearfix hack", `overflow`, or the modern method of `display: flow-root` on the parent container to fix these problems.

## Positioning
The `position` property is another very useful layout tool for removing objects from normal flow. Elements in normal flow actually already have a position value defined: `static`. 

`position: relative` is very similar to `position: static` but allows us to alter the element's final position by using `top`, `bottom`, `left`, and `right`. Defining these directions will counterintuitively move the element in the opposite direction; think of it as a force in that direction pushing the object the other way.

`position: absolute` completely removes elements from normal flow, placing them on their own layer sitting on top of the rest of the page. Other elements ignore any would-be spacing. The directional properties work a little bit differently now too; they specify the distance the element should be from each side of the containing element. We can change which element the absolutely positioned element is relative to by adding a position to the parent container.

When multiple elements are absolutely positioned, it becomes tricky to figure out which one overlaps the other. The `z-index` property sets the z-axis position of elements and can control which one is on top or bottom.

`position: fixed` is useful for navigation headers and footers. It works like absolute position but fixes an item to a position in the viewport, so it cannot be scrolled past. 

The last kind of positioning is `position: sticky`. This acts like relative positioning until a certain scroll point is reached, at which point the element becomes fixed to the screen.

## Multiple-Column Layout
Use `column-count` or `column-width` in a container to turn on multicol. The columns have flexible widths.

To style columns, we can use `column-gap` to add gaps and `column-rule`, a shorthand, to style rules between the columns. The rule doesn't take up its own width but instead sits in the middle of the gap.

Items in columns can fragment and become messy to look at. To fix this, we use properties from the CSS Fragmentation specification like `break-inside: avoid` or `page-break-inside:avoid` on the column items.