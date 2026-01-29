#html #webdevelopment
# Introduction

Hyper-text markup language (HTML) describes the structure and content of a webpage, while CSS styles that page. Javascript makes a webpage interactive and responsive. This page describes HTML5.

Here is a very basic HTML page format

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Obsidian HTML Page</title>
  </head>
  <body>
    <h1>Hello, Obsidian!</h1>
    <p>This is a basic HTML page rendered from within Obsidian.</p>
  </body>
</html>
```

## Basic Points

* `<!DOCTYPE html>` - Doctype declaration, allows us to tell which version of HTML we're using; in this case, HTML 5
* `<html> ... </html>` indicates the start and stop of HTML content of the page
* `<head> ... </head>` element describes stuff not in the main body, but other information for the browser such as
	* `<title>`
* `<body> ... </body>` is the visible part of the page
* HTML is consistent of a bunch of nested HTML <b><u>elements</u></b> which are indicated by HTML tags, indicated by the angled brackets `<blah>`. An open tag begins the element and a close tag, indicated as `</blah>` ends the element. 
* Leave comments with the following syntax <!-- I'm a comment -->

HTML elements are structured according to the #documentobjectmodel , or DOM, which is a tree-like structure that describes how all HTML elements are related to each other. Elements can have parent or child elements. This is helpful for understanding the page, but also for when using <b><u>JavaScript</u></b>. 
### Attributes

<b><u>Attributes</u></b>, for example in the case above in the `<html>` tag, `lang="en"` tell the web browser that the language is english. Attributes can help clarify HTML elements, and tell the browser to adjust the behavior of an element.

An attribute is a value placed inside an opening HTML element tag. 
e.g. `<element attribute="value"></element>`

## Header

The header of an HTML page should contain the following
```
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Examples of the link element</title>
  <link rel="stylesheet" href="./styles.css" />
</head>
```

Where
* `<link rel="stylesheet" href="./styles.css" />` - This links to a CSS stylesheet
	* rel - specifies that the relationship is to a stylesheet

## Other Common Tags

### Headings 
`<h1> ... </h1>` - this is a H1 heading, which indicates a major section of a page. This is the largest heading, and they continue on down to `h7` or `h6` generally, gradually getting smaller. Only one should be used per page. 

### Paragraph
`<p>...</p>` is used for basic text and paragraph stuff. 

### Div
`<div> ... </div>` is probably one of the most common dividers in HTML. This comes with no unique styling and is an extremely common way to group elements and objects together for whatever reason.

### Lists
Lists can be ordered (numbered) or unordered (bullets), and are denoted as follows

```
<ol> <!-- ordered list -->
	<li> ... </li>
	<li> ... </li>
	...
</ol>
<ul> <!-- unordered list -->
	<li> ... </li>
	<li> ... </li>
	...
</ul>
```

Lists can be nested in list item elements. 
### Images
Images can be inserted into pages, but require some mandatory attributes. It's also worth noting that there is no closing tag for an image. 

`<img src="/path/to/img.jpg" alt="image stuff">`

In this case, `src` indicates where the image is stored and `alt` is a text alternative to display when the browser can't render the image. `width` can also be an attribute to set size, more to see in CSS. 

### Links
Hyperlinks are the building blocks of the internet and can obviously be included in HTML. It's represented with an anchor tag:

`<a href="https://google.com" target="_blank">Click Here</a>`

Where `href` is short for hyperlink reference; which can also point to an image. The text in-between the open and close tags will be the text replacement for the actual hyperlink. Note that the `target` attribute is optional but can tell the browser where to open a link, such as in a `_blank`, or new tab.

**Note**: Even though images and links feel similar, make sure to note the differences including the tags (images being void) and src/href differences. 

##### More links

Links are also used (as seen above) for stylesheets and can also include links to fonts

`<link rel="preconnect" href="https://fonts.googleapis.com" />`

Where `preconnect` value for `rel` tells the browser to create an early connection to speed up loading. 

Links can also be used for icons

`<link rel="icon" href="favicon.ico" />

Where `favicon` is a favorite icon used commonly in the doc, like a logo. 
### Tables
HTML represents tables in an enumerative way based on rows and cells.

```
<table> <!-- define a table element -->
	<thead> <!-- the table header to define columns -->
		<tr> <!-- a table row -->
			<th>Column 1 title</th>
			<th>Column 2 title</th>
			...
		</tr>
	</thead>
	<tbody> <!-- the body is where the bulk of the table exists -->
		<tr>
			<td>Data point 1</td> <!-- a table data cell -->
			<td>Data point 2</td>
			...
		</tr>
		<tr>
			<td>Data point 3</td>
			<td>Data point 4</td>
			...
		</tr>
	</tbody>
</table>
```

### Forms
Users can input information to websites. Forms have two data types, the information and a submit button. Input tags have no closing either. 

```
<form>
	<input type="text" placeholder="Some Text" name="Input1">
	<input type="submit">
	<input type="checkbox" checked> <!-- Pre-checked box -->
</form>
```

Input tags are defined as
* Type defines the datatype including text, password, radio, and submit buttons
* Placeholder shows up in the empty field and can be used to prompt a user to input a certain piece of information
* name is how the input will be tracked in the backend

Additionally, datalist elements can be added to include dropdowns that will autocomplete based on input. These are common in uses such as selecting a country of origin or U.S. state for shipping. 

## Tips

You can open the page in a browser with this shortcut
`open {page}.html`

HTML Notes
* It's best practice to use lowercase even though HTML is case insensitive
* Elements without a closing tag are called "void elements"
	* Sometimes they have a `/` such as `<img />` , which does nothing but is seen in the world occasionally.
* Alternate descriptions are useful even when not normally seen in case someone with a disability visits a website. 

Boolean Elements - these specify the state of an HTML attribute. Note that they are simply put as they are, no extra syntax like "" or = or anything. 
* disabled
* readonly
* required


