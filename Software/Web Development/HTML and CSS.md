#html #css #webdevelopment
# Introduction
Note: for this we're talking about HTML5 and CSS3

# HTML

Hyper-text markup language (HTML) describes the structure of a webpage, while CSS styles that page. 

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
* <b><u>Attributes</u></b>, for example in the case above in the `<html>` tag, `lang="en"` tell the web browser that the language is english. Attributes can help clarify HTML elements. 

HTML elements are structured according to the #documentobjectmodel , or DOM, which is a tree-like structure that describes how all HTML elements are related to each other. Elements can have parent or child elements. This is helpful for understanding the page, but also for when using <b><u>JavaScript</u></b>. 

## Other Common Tags

### Headings 
`<h1> ... </h1>` - this is a H1 heading, which indicates a major section of a page. This is the largest heading, and they continue on down to `h7` or `h6` generally, gradually getting smaller.

### Lists
Lists can be ordered (numbered) or unordered (bullets)



## Tips

You can open the page in a browser with this shortcut

```
open {page}.html
```


