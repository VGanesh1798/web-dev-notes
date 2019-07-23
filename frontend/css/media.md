# Media Queries
Media queries are useful when you want to apply different styling based on the screen type or viewport size. They are used to:
- apply different styling based on the `@media` and `@import` at-rules
- to target specific media in `<style>`, `<link>`, `<source>`, and others with the `media` attribute
- To test and monitor media states with the `Window.matchmedia()` and `MediaQueryList.addListener()` methods

The basic syntax is the same for all media queries.

## Syntax
- Media queries are composed of a media type and any number of media feature expressions
- Multiple queries can be combined using logical operators

The media types are as follows:
```
all      # Intended for all devices
print    # Intended for paged material
screen   # Intended primarily for screens
speech   # Intended for speech synthesizers
```
A couple of the media features:
```
height            # Height of viewport
width             # Width of viewport
orientation       # Orientation of the viewport
inverted-colors   # Checks if the user agent or OS is using inverted colors
hover             # Checks if user is allowed to hover over elements
scripting         # Checks if Javascript is available
```
Lastly, the logical operators:
```
and    # Combines multiple queries into one and joins media features with types
not    # Negates media query
only   # Applies style only if entire query matches
,      # Combines multiple queries into a single rule
```