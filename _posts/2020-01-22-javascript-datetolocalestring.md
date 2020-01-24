---
image: "/assets/default-social-image.png"
title: JavaScript date.toLocaleString()
categories: JavaScript-date
---

The date.toLocaleString() is a built-in JavaScript function that is used to convert a date and time to a string.

**Syntax:**

```
dateObj.toLocaleString(locales, options)
dateObj should be a valid Date object.
```

**Parameters:**

**locales:** This parameter is an array of locale strings comprising one or more locale or language tags and the parameter is optional. Specify the language in the locale argument if you want to use a specific language format in your application.
**Options:** It is also an optional parameter and includes properties that define the options for comparison. Some properties are localeMatcher, timeZone, weekday, year, month, day, hour, minute, second etc.

**Return values:**

It returns the date and time as a string value in the particular format defined by locale.

Example 1:

This code prints the date and time for the current. Also, the toLocaleString() method does not use any parameter in this code, so it uses the locale conventions of the operating system and returns the result that is machine-specific.

```
<script> 
  var d = new Date(); 
  var result = d.toLocaleString(); 
  document.write("date and time as a string =  " + result); 
</script> 
```
   
Output:

`date and time as a string = 6/26/2018, 10:28:17 `

Example 2:

This code prints the date and time specified by the locale parameter in a string format.

```
<script> 
  var date = new Date(Date.UTC(2018, 5, 26, 7, 0, 0));   
  var options = { hour12: false };   
  document.write(date.toLocaleString("en-US")); 
  document.write("<br>"); 
  document.write(date.toLocaleString("en-US", options)); 
</script> 
```

Output:

```
6/26/2018, 12:30:00 PM
6/26/2018, 12:30:00
```

Note :

The toLocaleString() method varies from toLocaleDateString() in the aspect that toLocaleDateString() only converts the date of an object to a string, while toLocaleString() converts the date and time to a string.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari