---
image: "/assets/default-social-image.png"
title: JavaScript Window print() Method
categories: JavaScript-functions
---

JavaScript page printing is a basic JavaScript code used to print web pages content.

* The print() function prints the current window contents.
* It essentially opens the Print dialog box, enabling you to choose between different options for printing.

**Syntax:**

`window.print()`

**Parameters:** Not required

**Returns:** This doesn't return anything

The following Javascript code displays a print button and then the property of that web page is shown in a sheet where you will print it.

The window.print() function in JavaScript is used to execute the operation.

Example :

```
<!DOCTYPE html> 
<html> 
  
<head> 
    <title> 
        HTML | DOM Window Print() method 
    </title> 
  
    <script type="text/javascript"> 
    </script> 
  
</head> 
  
<body> 
  
    <h2>Hello World</h2> 
    <form> 
        <input type="button" value="Print" 
               onclick="window.print()" /> 
    </form> 
  
</body> 
<html> 
```

Nevertheless, the web pages are not restricted only to text. There are also other items on the web pages, such as pictures in different colors, etc. It is possible to print these pages in the following ways:

* Take a copy of the page and cut out unnecessary text and illustrations, and then transfer it from the original to the printer-friendly version. It ensures that the entire page will be written as you saw the document being displayed as it is without any alteration, if you see a commercial, it will also be printed in it.
* If you don't want to keep an extra copy of a page, label the printable text with appropriate comments such as PRINT STARTS HERE..... PRINT ENDS HERE and then the PERL or any other script in the background can be used to purge printable text and show that for final printing. It ensures that the component chosen will be printed

Supported browser: Window print() method-supported browser is described below:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safri