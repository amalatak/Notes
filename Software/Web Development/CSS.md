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

### Styling Hierarchy
Multiple elements can be called and styled, which creates a problem in CSS called *specificity*. Specificity is ordered as
1. in-line
2. id
3. class
4. type

### More Selectors
The ways of referencing HTML elements in CSS discussed above is not limited to that. Idk google them, don't really care enough to add them here. 


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