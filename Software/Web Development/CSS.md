#CSS #webdevelopment 
# Introduction
Cascading Style Sheets (CSS) tells a webpage how to style HTML elements. 

CSS can be included in the HTML file by including a style #attribute in the HTML #element tag to change the #properties, such as color or alignment, of a given element from their default values. 

`<h1 style="color: blue; text-align: center;">Some Text</h1>`

Where in the above example we set the color of an h1 element text to blue and the alignment to center; but generally, HTML and CSS are stored separately and linked by TBD.

# Linking CSS to HTML
While CSS can be included as mentioned above, it's more common to see it included in the header (still less likely) or most importantly in separate files

### Header Inclusion
You can insert CSS like so in the header (under the `<head>` tag) to alter an h1 as example. 
```
<style>
	h1 {
		color: blue;
		text-align: center;
	}
</style>
```
### CSS File
This works best for websites that have multiple pages with common stylings that way you can include a CSS file instead of a giant header at the top of every HTML page. 

Create a new file with the `.css` extention, let's assume it's called `style.css`

```
h1 {
		color: blue;
		text-align: center;
	}
```

And then include the code in the html page header (under the `<head>` tag) using a stylesheet link

```
<link rel="stylesheet" href="/path/to/styles.css">
```
# Syntax and Structure

### Attribute Styling
Attributes are usually set with the following pattern

`attribute-name: configuration_or_style;` 

And how an attribute can be styled may have several options. For example colors can be set as plain text common colors or as actual hex code (e.g. 30a401 or something).

Styles also flow down from the highest level element given the attribute styling (hence the cascading part). For example a styled `body` tag with `div` elements within it will be given any styling in the `body` that isn't explicitly changed in the `div`.

### Elements
HTML elements are all of the basic building blocks of HTML. Elements are generally referenced in CSS to style like so
```
element {
	atttribute: styling some-style, more-styling some-more-style;
}
```

And they can be grouped as
```
element-1, element-2 {
	...
}
```

### IDs
HTML elements can be given any ID there is, but they must be unique. 

`<h1 id="foo">Heading 1</h1>`

Which makes the specific element easier to give its own attributes. They can then be referenced in CSS with a pound/hash sign

```
#foo {
	color: blue;
}
```

### Class
IDs must be unique but can technically be given to multiple elements to style groupings making it a class.

```
<h1 class="bar">Heading 1</h1>
<h1 class="bar">Heading 2</h1>
```

And the CSS would look like

```
.bar {
	color: blue;
}
```

### Pseudoclass
There are classes that might only apply when an element is in a given state, such as when a cursor is hovering over it for example.

```
----- CSS -----
button {
	width: 200px;
	height: 50px;
	font-size: 24px;
	background-color: green;
}

button:hover {
	background-color: red;
}
...
----- HTML -----
<button>
	Click Me
</button>
```

### Styling Hierarchy
Multiple elements can be called and styled, which creates a problem in CSS called *specificity*. Specificity is ordered as
1. in-line
2. id
3. class
4. type

### More Selectors
The ways of referencing HTML elements in CSS discussed above is not limited to that. There are many but a few examples are:

* Descendent selectors - can select if one item is nested in another
* Direct descendent selectors - can select if one item is directly nested below another item
* Attribute selectors - select based on an attribute
	* e.g. `a[href="https://google.com"] { ... }`

# Responsive Design
It's important to style web pages dynamically based on web page viewing medium or method. Phone screens will look different than laptop screens will look different than tablets.

The <b>viewport</b> is the portion of the screen that displays content to a user. We can adjust for this by adding the following to the html page

`meta name="viewport" content="width=device-width, initial-scale=1.0"`

This changes the viewport to be the width of the device. 

### Media Queries
These help control how pages look depending on how the page is rendered or how big the screen is. We can check whether a page is vertical or horizontal, or whether the user is viewing on a computer or printout. We can adjust the color, padding, margin, make something visible or invisible, etc. 

Here is an example that changes a h1 color based on screen width.

```
----- CSS -----
@media (min-width: 600px) {
	h1 {
		background-color: red;
	}
}

@media (max-width: 599px) {
	h1 {
		background-color: blue;
	}
}

----- HTML -----
<h1>Hello World</h1>
```

### Flexbox
This is helpful for displaying elements on a page in different ways based on screen size. 

```
----- CSS -----
#container {
	display: flex;
	flex-wrap: wrap;
}

#container > div {
	background-color: green;
	font-size: 20px;
	margin: 20px;
	padding: 20px;
	width: 200px;
}
----- HTML -----
<div id="container">
	<div>1. Some sample text</div>
	<div>2. Some sample text</div>
	<div>3. Some sample text</div>
	...
	<div>n. Some sample text</div>
</div>
```

This code generates a series of HTML elements that are boxes. They each have a given size, but have been styled with flexbox such that each element will remain a fixed width and wrap the browser-width to show up as a grid of different dimensions. 

### Grid Layout
Another way to layout elements is using a grid

```
----- CSS -----
#grid {
	background-color: green;
	display: grid;
	padding: 20px;
	grid-column-gap: 20px; 
	grid-row-gap: 10px;
	grid-template-columns: 200px 200px auto;
}

.grid-item {
	background-color: white;
	font-size: 20px;
	padding: 20px;
	text-align: center;
}
----- HTML -----
<div id="grid">
	<div class="grid-item">1</div>
	<div class="grid-item">2</div>
	<div class="grid-item">3</div>
	...
	<div class="grid-item">n</div>
</div>
```
# Bootstrap
CSS styling doesn't need to be done from scratch every time, and probably not a lot at all. A popular CSS library for implementing that concept is Bootstrap. 

Bootstrap can be included in a web page and by including a certain class in a div

`<link rel="stylesheet" href="bootstrap_link">`

where `bootstrap_link` is taken from [their website](https://getbootstrap.com). That class can assume styling of Bootstrap such as

* Alerts
* Tables
* Buttons
* etc

Bootstrap is also mobile-adaptive, with element options for sizing based on screen size. 

# Common CSS Tools
There are many frameworks and different CSS methods you can use to style pages, but here are a few major examples
### Size
You can change the size of elements like so (note that this is the element and not the content)

HTML:
```
<div>
	Some Text
</div>
```

CSS
```
div {
	background-color: blue;
	width: 100px;
	height: 400px;
}
```
### Content Location
Within an element, you can move around stuff with padding. Using the same div example as above.

```
div {
padding: 20px;
}
```

This adds padding on all sides within the element; but an element can be padded on the outside with margin:
```
div {
	margin: 20px;
}
```

### Appearance

We've seen `color` and `background-color`, but here are some other examples

Font can be changed with font-family, which has options for backup fonts if a browser can't render the first choice. Font size and weight can be changed as well.
```
div {
	font-family: Arial, sans-sarif;
	font-size: 20px;
	font-weight: bold;
}
```

You can also add a border, the following would be solid and black.
`border: 3px solid black`

If using a table with a bunch of cells you can add a border to each of them, but it will look like a bunch of boxes. It will look more like a table using collapse
```
table {
	border: 1px solid black;
	border-collapse: collapse;
}

td, th {
	border: 1px solid black;
}
```


Follow up with Chris about NASA security standard
Follow up on latency requirement if not being accounted for, ask antenna providers to give us timestamps if now
Follow up with FSW about testing launch pad connections on MK1
Check AAA requirements for flight voc restrictions
Talk to people about packet loss requirement