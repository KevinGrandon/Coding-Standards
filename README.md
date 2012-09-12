# About

This style guide is intended to provide a place to gather my thoughts around coding standards. For now this guide is mainly focused on frontend technologies, but other disciplines and languages may be added in the future.

As ideas, best practices, and standards continue to emerge and evolve - so shall this guide. Very few things in this guide are considered "the law", and many folks will not agree with everything here. That said, I'd love to hear any feedback or recommendations that you may have.

## Contents

* [CSS](#css)
* [HTML](#html)
* [Javascript](#javascript)
* [Comments](#comments)

## CSS

### Spacing

* Insert a single space after : in declarations.
* Tabs or spaces should be 4 characters in width. (I prefer tabs)
* Ensure there is one space before the final selector and opening {
* One selector per line
* One css property/value pair per line

### Casing

As CSS features hyphen-delimited syntax, we recommend adhering to that standard. Nowhere in CSS do you see CamelCase, camelBacked, or lower_and_underscored syntax. We think it's best to stay consistent here. Take the following example:

   ```CSS
/* Camel backed (bad) */
#contentList { /* Using one format here */
    font-weight: bold; /* And another here */
}

/* hyphen-delimited (good) */
#content-list {
    font-weight: bold;
}
```

### Property Values

* For colors, use hex color codes, short-codes are fine where supported: `#FFF`
* Consider bytes over the wire. It's generally less bytes to have a single padding rule, instead of padding-left and padding-right for example.

```CSS
a {
    margin: 10px 0 0 10px;// Instead of margin-top and margin-left
    padding: 10px 0 10px; // Leave off unnecessary values
    color: #FFF; // Shorthand syntax 
}
```

### Declaration Ordering

Try to follow the following order where possible. If all developers know the general area that a property may appear, productivity should be increased. The general rule of thumb is in this order:

* Display and positioning
* Box model
* Background
* Fonts and colors
* Other


```CSS
div {

    // Display attributes first
    position: absolute;
    z-index: 1;

    // Box model (outside to inside)
    margin: 0 auto;
    border: 1px solid #000;
    padding: 10px;
    width: 100px;

    // Background
    background: #FFF;

    // Colors and Typography
    font-size: 12px;
    color: #FFF;
}
```


## HTML

### Tags

* Lowercase tag and attribute names
* Use data- attributes where applicable
* Avoid using custom attributes
* Do not use inline event hooks such as onclick or onload

``` HTML
<div class="good-tag"></div>

<div data-sauce="bbq"></div>
```


### Indenting

All nested tags should be indented. Avoid nesting multiple block level elements on one line.

``` HTML
<div>
    <b>Some indented text</b>
</div>
```

### Doctype

Generally you want to use the HTML5 doctype.

``` HTML
<!DOCTYPE html>
```

### Quotes

All HTML tag attributes should use double quotes (").

``` HTML
<a href="#" class="btn">My Link</a>
```

### Self-closing Tags

This guide assumes that you are serving HTML5 content, and thus there is no need for the closing slash in self closing elements. Here are some examples of self-closing tags without the closing slash.

```HTML
<br>
<hr>
<img>
<input>
<link>
<meta>
```

## Javascript

### No Semicolons

Javascript provides for automatic semicolon insertion. Learn it, and embrace it. In addition to increased productivity, it makes for cleaner code.

``` JS
var foo = function() {
    return true
}

alert(foo())
```

### Casing

* Use CamelCase for names of classes and prototypes.
* Use camelBacked for variables and methods.

``` JS
// Demonstrating proper use of casing in Javascript 
function Car() {
}

Car.prototype.pressBrakes = function() {}

var clunker = new Car()
```


### Variables

It's highly recommended, but not required, that all variable statements in a block be declared at the top of the block. Use a single statement where it makes sense, or logical groupings of statements otherwise.

``` JS
// Not ideal, using multiple var statements
function foo() {
    var sauce = 'bbq'
    var leet = false
}

// Correct, a single var statement
function foo() {
    var sauce = 'bbq',
        leet = true,
        aligned // Align variable names where possible
}
```

Favor Object and Array literals instead of instantiation.

``` JS
// Use the literal {} instead of new Object()
var sauce = {}

// Use the literal [] instead of new Array()
var pies = []
```


### Braces on the same line

There are very few required rules as part of this document, but this is one of them. Due to automatic semicolon insertion, we are required to use braces on the same line as statements. Take the following example:

``` JS
// Bad code
var foo = function()
{
    return
    {
        cheese: 'burger'
    }
}
```

Javascript will stick a big ugly semicolon right after that return statement, before the object literal. The result of calling foo() will always be undefined.

``` JS
// Bad code
// What Javascript sees
var foo = function()
{
    return; // <- It just stuck this big semicolon here, wtf?
    // We never execute code beyond the return statement.
    {
        cheese: 'burger'
    }
}
```

Here's an example of how we should structure the function:

``` JS
// Good code
var foo = function() {
    return {
        cheese: 'burger'
    }
}
```

### Comma Style

Either leading or trailing styles of commas are fine. Work with your team to see which makes more sense and stick to one style. The leading comma style is fairly new, but gaining momenteum. Some people believe it allows for easier debugging and editing of code.

The recommendation is that you use 'blocking' to align variable names where possible.

``` JS
// Trailing comma approach
var sauce = 'bbq',
    comma = 'trailing',
    aligned

// Leading comma approach
var sauce = 'bbq'
  , comma = 'trailing'
  , aligned
```

## Comments

Well formed comments should be provided for every function and class definition. A class/function level comment should follow the format of:

```Javascript
/**
 * Comment should begin with a slash and 2 asterisks.
 * Parameters should follow with the following format
 * @param type description of parameter
 * @return type
 */
```

The double slash method of comments may be used within javascript code for information which may be useful to developers.