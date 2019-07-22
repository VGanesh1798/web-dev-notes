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

