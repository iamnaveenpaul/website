---
image: "/assets/default-social-image.png"
title: Understanding basic JavaScript codes.
categories: JavaScript-basics
---

**Understanding basic JavaScript codes.**

Injecting JavaScript into a web page is like adding any other content of HTML in it. The `<script>` and `</script>` tags used to add JavaScript to HTML. A script blog is named the code followed by the tags `<script>` and `</script>`.

The tag `<script>` can be put between the tags `<head>` and `</head>` or between the tags `<body>` and `< /body>`.

The most important attribute of the `<script>` tag was the 'type' attribute. It's no longer being used, however. Browser knows the JavaScript code is inside the `<script>` tag.

`<script type="text/javascript">`

**How to write, save and run codes:**

Method 1:

1. To compose the code, use any note editor such as Notepad, Notepad++
2. Save the .html file and load it into your web browser

Method 2:

1. Make a.js file and use your preferred editor to compose your JS script into this file.
2. In the HTML file, insert `<script src="relative_path_to_file/file_name.js"></script>` at the end of the `<body>` tag.

**Code for Painting the page light blue**

```
<!DOCTYPE html> 
<html> 
  <head> 
    <title></title> 
  </head> 
  <body bgcolor="white"> 
   <p>Paragraph 1</p> 
   <script type="text/javascript"> 
   document.bgColor ="lightblue"; 
   </script> 
  </body> 
<html> 
```

The web-page theme is light blue, but the opening body tag is set to a white background color.

`<body bgcolor="white"> `

The page's background color is light blue because JavaScript is used to change the background color of the file to be light blue.

`document.bgcolor="lightblue";`

**Learning from the code:**

1. Page is referred to as a document of scripting on a web page.
2. Document properties can be accessed by writing document accompanied by a dot, followed by the name of the property. There are loads of properties in the file.
3. After the browser's <script> tag starts interpreting the text as JavaScript until the </script > drops in.

**Code to write something to a web page using JavaScript:**

Let's just type "Hello World!"using JavaScript to a blank page.

```
<!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0 
 Transitional//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”> 
 <html xmlns=”http://www.w3.org/1999/xhtml”> 
  <head> 
    <title></title> 
  </head> 
  <body> 
   <p id="ResultsP"></p>  
   <script type="text/javascript">//Script Block 1 
   document.getElementById('ResultsP').innerHTML ='Hello World!'; 
   </script> 
  </body> 
<html> 
```

**Learning from the code:**

#1. This code has been added to the following line.

```
 <!DOCTYPE html PUBLIC “-//W3C//DTD XHTML 1.0
 Transitional//EN” “http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd”>
 <html xmlns=”http://www.w3.org/1999/xhtml”>
```

It makes it known to the web browser that the user requires XHTML. In fact, it does not make any difference to the code; without the extra lines it would work just fine.

#2. Remember that the id attribute has been given to the `<p>` tag.

`<p id=”ResultsP”>`

This id must be distinctive on the web page because the JavaScript uses it in the following line to identify the specific HTML element:

`document.getElementById(‘ResultsP’).innerHTML = ‘Hello World!’;`

The code simply says: "Get me the document element with id ResultsP and set the HTML to Hello World within that element!”

It is important that the code that accesses the paragraph is otherwise after the paragraph, the code would attempt to access a paragraph before it existed on the page and make an error.