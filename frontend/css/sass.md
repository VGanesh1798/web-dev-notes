# SASS
SASS stands for **S**yntactically **A**wesome **S**tyle **S**heets; it is a CSS preprocessor that is interpreted into CSS but has a much nicer syntax and some extra features.

You can read extensively about SASS in its [documentation](https://sass-lang.com/documentation).

## Variables
SASS offers the use of variables in CSS, which can be set to numbers, strings. colors, or booleans. The variable names can then be used in future rules instead of values. Variables are declared using `$` at the start of the name and a colon separates the name from the value. Variables can either be global or local to a block's scope.

## Nesting
In SASS, rules can be nested inside of other rules, which improves readability greatly. Nesting also works for namespaces and parent references.

## At-rules
SASS has a number of at-rules, including the following:
- `@import` imports another stylesheet
- `@while`, `@for`, and `@each` allow for looping mechanisms in styling
- `@if` and `@else` for conditional flow
- `@function` to define a SASS function
- `@mixin` and `@include` to create a mixin and then include it elsewhere
- `@extend` to improve inheritance

## Operators
SASS has support for operators like `+` and `/` to perform mathematical operations on property values. Combined with variables this can be a very powerful tool.