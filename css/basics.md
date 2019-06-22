# CSS Basics
CSS stands for **C**ascading **S**tyle **S**heets. It is not a programming language but is instead a styling language that affects markup languages like HTML to change the look and feel of elements. Combined with HTML, CSS forms the Document Object Model, also called the DOM. CSS can be thought of as the "clothing" of a website.

## Anatomy and Syntax of CSS
CSS can be applied directly in HTML by using `<style>` tags or inline using the `style` attribute, although this second method is bad practice. Typically, CSS is imported from .css files using `<link>` tags in the header of an HTML file.

CSS consists of properties and values, which paired together are called declarations. These declarations are applied to selectors to form rules. The property is separated from its value by a colon, and declarations are separated by semicolons. All declarations for a selector are placed in brackets.

Aside from rules, CSS also has statements. A common statement is the at-rule, specified by an '@' symbol. Examples of at-rules are `@import` and `@media`. Rules can be nested inside of these statements.

Comments in CSS are made using `/*` and `*/`.

## Selectors
The most basic selector in CSS references an element of HTML, like `<h1>` or `<p>`. Class selectors are more specific, selecting only elements with a `class` value. These selectors consist of a dot followed by the class name. ID selectors are even more specific since `id` values cannot be shared among elements. These selectors consist of a hash symbol followed by the ID name. On the opposite end of the spectrum is the universal selector `*`, which selects every element on the page. It is most useful when building combinators.

Attribute selectors match elements based on the values of their attributes. To form them, use square brackets containing the attribute name to match to any element with that attribute. To be more specific, you can use `[attr=val]` to match attributes with a particular value, or `[attr~=val]` to match attributes containing a value in a list of words. Attribute selectors can also match similar to regular expressions. `[attr^=val]` matches values starting with `val`, while `[attr$=val]` matches values ending in `val`. To match any substring, use `[attr*=val]`.

A pseudoclass is a keyword added to a selector to match elements when they are in a particular state, like when the mouse hovers over them. They are separated from selectors by a colon. A pseudoelement is a similar keyword that is separated from a selector by two colons.

Combinators are formed by combining selectors and allow for more fine-grained tuning. A descendent combinator `A B` (A and B are selectors) is for any element matching B that are descendents of elements matching A, while a direct child combinator `A > B` is more specifically only the first descendents. An adjacent sibling combinator `A + B` is for elements matching B that are next siblings of elements matching A, while the general sibling combinator `A ~ B` is, well, more general.

Selectors can be grouped with commas to apply the same rules to multiple selectors.

## Values and Units
Numeric values are some of the most common in CSS, being most used to style the size of elements. The most commonly used absolute unit for measurement is `px` for pixels, and the most commonly used relative unit is `em`. `1em` is the same as the font-size of the current element, which defaults to `16px`. Elements which inherit font-sizes from their parents can be tricky to work with when using `em` units. `rem` is a more useful variant of `em` since inherited font-sizes have no effect on it, but older versions of Internet Explorer don't support it. Screw Internet Explorer.

Some numerical values can be unitless, especially when expressing the value `0`. `line-height` is a property that can take unitless numerical values to act as a sort of multiplying factor.

Percentages are useful when trying to resize things based on the size of the parent element. Layouts using percentages can be called **liquid layouts** because the layout changes as the viewport changes; the opposite layout is a **fixed-width layout**.

Colors can be expressed in a multitude of ways in CSS, with one common method being to just use keywords like `red` or `black`. These base colors look pretty ugly though, so hexadecimal codes are a better option since there are over sixteen million color codes to choose from. The `rgb()` function can be used instead of hex codes and is a bit easier to understand. Colors can also be picked using `hsl()` for hue, saturation, and lighting. To add transparency into the mix, use `rgba()` or `hsla()` and set the alpha value accordingly. Another option is to use the `opacity` property (useful when using hex codes).

`rgb()` and `hsl()` are examples of functions, and other CSS functions include `calc()` and `url()`.

## Cascade and Inheritance
What does "Cascade" even mean? Essentially, the Cascade controls what rules are inherited from parent elements, and at a basic level this means that the order of rules matters. At a more detailed level, this means that selectors win out based on importance, specificity, and source order, in decreasing order of weight.

Importance can be manually overriden by using the `!important` declaration on a rule. Even if a rule would be inherited by a child element, this keyword can override that. Usually, it's not a good idea to use `!important`.

As discussed earlier, specificity also matters. ID selectors are the most specific kind of selector, so they win out in these situations unless `!important` is used.

Lastly, source order matters. Later rules will override older ones, such as when two rules for `p` are written. This wording is a bit misleading, however; rules aren't what get overriden, but *properties* are. Properties in an older rule that aren't reassigned later will continue to work.

Not all properties are inherited by children elements. It makes sense for `color` and `font-family` to be inherited, but not `margin` or `padding`. Four special values are used to control inheritance manually. Using `inherit` makes the child always inherit that property value, and `initial` makes the property use the browser's default stylesheet value (it defaults to `inherit` when the browser doesn't have a value specified). `unset` resets the value back to its natural value, and `revert` reverts the property back to the value it would have had before additional styling was done. The shorthand property `all` can be used to apply one of these settings to almost all properties at once.

## Box Model
CSS styling adheres to the box model, where each element is represented as a box stacked on top of other boxes. These boxes of `length` and `width` have multiple layers around them, consisting of `padding`, `border`, and `margin`. 

Using absolute units can sometimes cause box content to spill out and overflow. To control this behavior, use the `overflow` property.

Background images and colors naturally extend to the outer edge of the box border, which can be annoying sometimes. To change this, use the `background-clip` property to control how far the background extends.

Boxes also have an `outline`, which is not part of the box model but is often used for accessibility reasons to highlight active items.

Boxes also have a `display` that affects how they stack. `block` elements stack on top of one another and `inline` elements wrap around the page, flowing with text. A third type is `inline-block`, which sort of combines the flowing nature of inline boxes but can have its height and width affected like block boxes.