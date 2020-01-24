---
image: "/assets/default-social-image.png"
title: JavaScript date.toLocaleDateString()
categories: JavaScript-date
---

The date.toLocaleDateString() is a built-in JavaScript function that is used to convert a date to a string.

Syntax:

`dateObj.toLocaleDateString( [locales][, options])`

dateObj should be an object with a valid Date.

**Parameters:**

locales: This parameter is an array of local strings containing one or more languages or local tags. Bear in mind that this is an optional parameter. Should you decide to use a specific language format in your application, mention that language in the locales argument
options: This is also an optional parameter which contains property that define options for reference. Some of the properties are localeMatcher, timeZone, weekday, year, month, day, hour, minute, second, etc.

**Return values:**

This returns a date in a specific format, as a string value specified by the locale.

Example 1:

This code has the current date printed out.

```
<script> 
var dateObj = new Date();  
var options = { weekday: "long", year: "numeric", month: "short",  
    day: "numeric" };  
document.write(dateObj.toLocaleDateString("en-US")); 
document.write("<br>"); 
document.write(dateObj.toLocaleDateString("en-US", options)); 
</script> 
```

Output:

```
6/24/2018
Sunday, Jun 24, 2018
```

Example 2:

It uses the rules of the locale of the operating system without parameters return value of this process can not be depended upon in scripting.

```
<script> 
var dateObj = new Date(1993, 6, 28, 14, 39, 7); 
document.write(dateObj.toLocaleDateString()); 
</script> 
```

Output:

`7/28/1993 `

Note: Arguments for locales and options are not supported in all browsers. We can use the following function to check whether it is supported or not:

```
function toLocaleDateStringSupportsLocales() 
{ 
    try { 
        new Date().toLocaleDateString('i'); 
    } 
    catch (e) { 
        return e.name === 'RangeError'; 
    } 
    return false; 
} 
```

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari