# HTML Forms

Forms are an incredibly useful part of any website, allowing users to directly interact with the content on the website. They require Javascript to actually have any function and can get very advanced.

## Form Basics
Forms are all wrapped in `<form>` tags and have the attributes `action` to define a URL to send form data to and `method` to define the HTTP method used. Inputs are added using `<input>` tags, which are empty and can take on a variety of interesting functions. Inputs are inline elements by default. To add a large text box input, use the `<textarea>` element; note that it is **not** empty, and a default value is defined in between the opening and closing tags instead of in a `value` attribute.

Buttons are added using `<button>` and can have one of three values for `type`: `submit`, which submits the form; `reset`, which resets all the input areas; and `button`, which does nothing but is useful when implementing custom functionality in Javascript.

Styling is incredibly important with forms. Aside from CSS files, it can be included directly in the HTML with `<style>` tags.

## Structuring Forms
To group widgets that share common functions and purposes, use the `<fieldset>` element. This field can be labelled using a `<legend>` element, which is placed right below the opening `<fieldset>` tag.

Inputs can have a `<label>` element with a `for` attribute, which references the `id` attribute of the corresponding input area. Inputs also have a `name` attribute, which is incredibly important as it is used as the key for the key/value pairs sent upon form submission.

Elements like `<div>` and `<p>` are commonly used to structure forms, with more complex forms using elements like `<h1>` or `<section>`.

## Native Form Widgets
All widgets have some common attributes like `disabled`, `autofocus`, `form`, `name`, and `value`. The `form` attribute is used to link external widgets to forms, but no browser actually supports this.

There are many `<input>` fields with different attributes based on the `type`. The default input type is `text`. Again, `<textarea>` can be used for larger input blocks.

Dropdown menus can be made using the `<select>` element, with multiple `<option>` elements corresponding to the choices. An option can be `selected` and the menu can have the `multiple` attribute on it to specify a multiple-choice menu. Autocomplete menus can be created by using `<datalist>` instead, and then attaching this element to an `<input>` field with a `list` attribute that references the list's `id`. Since some browsers don't support datalists yet, we can put a `<select>` inside the datalist and nest all of the options inside of this.

Checkboxes only send their data if they are checked; this contrasts with other inputs, which send data no matter what. Usually, checkboxes are placed as items of a list inside of a `<fieldset>` element with a corresponding `<legend>`. They are made using `<input>` elements with `type` set to either `checkbox` or `radio`, and an additional attribute is the `checked` attribute. Radio buttons with the same `name` are grouped together, and only one of the buttons can be selected at a time. The `value` of this button is then sent, and if no buttons are selected, no value is sent at all.

Buttons were described above. An `<input>` can also be used to make a button, but it is easier to style `<button>`.

More advanced `<input>` types include `number` and `range>`, which can (and should, for the slider) have `min`, `max`, and `step` defined. Sliders don't actually provide any visual indicator of what the selected value is; this has to be implemented using a `<span>` element and some Javascript. Date and time control exists in the form of types like `datetime-local`, `month`, `time`, and `week`. These can all be constrained using `min` and `max` too. Colors can be picked by using `color`.

Inputs can take files too, with the `file` type. The types of files to pick can be constrained using the `accept` attribute, and `multiple` can be used too.

To hide an input, use `hidden` for the type. A hidden input requires a `name` and `value`.

Inputs can also be set to `image` and will inherit all of the same attributes as `<img>`. These image buttons can be used to submit forms and send two key/value pairs. The keys consist of the `name` followed by the x and y coordinates of the click.

Progress bars can be inserted using `<progress>` and can have a `max` value. Meters are inserted using `<meter>` and are limited by `min` and `max`. They also take a `low` and `high`, as well as an `optimum`, to divide up the range of values and color the meter either red, yellow, or green depending on how optimal the current value is.

## Sending Form Data
Form data is sent using `action` and `method` and follows the HTTP protocol. The two most common methods are GET and POST. Using developer tools, we can track GET and POST requests and see headers such as `Host`, `Content-Length`, and `Content-Type`. The server-side language can receive and use this data in many different ways, and multiple frameworks exist to aid in these tasks.

When sending files, the POST method must be used and additionally, the `enctype` attribute for the form must be set to `multipart/form-data`. This changes the `Content-Type` header from the default value of `application/x-www-form-urlencoded`. The new value tells the browser that data has been split into multiple parts.

Sending form data often comes with security concerns like SQL injection. Don't ever trust users, and always check data.

## Form Validation
Although data should be validated on the server-side, the client-side does offer some form validation. A valid form input matches the `:valid` CSS pseudoclass and can be styled accordingly; its data will be sent upon submission, unless Javascript blocks this function. In contrast, invalid form inputs match the `:invalid` pseudoclass and submission will fail until the input becomes valid. The error message that appears can be changed using Javascript, by the way.

The `required` attribute is the simplest method of input validation. Another useful validator is the `pattern` attribute, which matches the input to a specified regular expression. The `minlegnth` and `maxlength` attributes can be used on text inputs much like `min` and `max` are used for numerical inputs.

Javascript is also used to validate forms on the client-side. The constraint validation API is useful in this regard, but the validation can be done without it (although this is much harder).

## Custom Form Widgets
We can combine HTML with CSS and Javascript to make our own form widgets. Javascript is unreliable technology however, so be wary of doing this. The DOM API is useful when adding functionality, but for browsers that have issues (like IE), libraries like jQuery are useful.

To make widgets accessible, we can use the `role` and `aria-selected` attributes.

## Sending Forms with Javascript
Modern HTML forms typically use Javascript to send the data rather than HTML itself. Data is typically sent asynchronously to only update the parts of the page that need to be updated. This method is called AJAX, with the 'X' standing for XML (although JSON is used much more now). `XMLHttpRequest` can be used manually in Javascript to send data, and the `FormData` object assists in making this simpler. `FormData` can be bound to a `<form>` element.

Another (bad) way to send form data is to build a form using the DOM API, putting the data in an `<iframe>`, and then retrieving the content from the iframe. It's a risky method for sure.

Lastly, when sending files, the `FileReader` API comes into use. 
