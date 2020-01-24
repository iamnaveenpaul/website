---
image: "/assets/default-social-image.png"
title: JavaScript date.toString() function
categories: JavaScript-date
---

The date.toString() is a JavaScript built-in function that is used to transform the contents of the provided date object into a string. The date object is generated using the date() constructor.

**Syntax:**

`dateObj.toString()`

Note: In the above syntax, DateObj is a valid Date object created using the conctructor Date() whose contents are converted to string.

**Parameters:**

This function needs no parameters. This is only used in conjunction with a Date object generated using Date() constructor whose content is transformed to a string.

**Return Values:**

The converted string is returned.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 15, 1996 05:35:32'); 
  
// Contents of above date object is converted 
// into a string using toString() function. 
var B = dateobj.toString(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`Tue Oct 15 1996 05:35:32 GMT+0530 (India Standard Time)`

**Errors and Exceptional cases**

Nothing is passed here as a parameter when generating date object but still it returns current day name, month name, date, year and time.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// Contents of above date object 
// is converted into a string 
// using toString() function. 
var B = dateobj.toString(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`Wed Apr 11 2018 00:50:44 GMT+0530 (India Standard Time)`

When passing some random value list, toString() returns the corresponding string produced.

The Date() Constructor format is identical to Date(month, date, year, time). In the program below, some values are provided by following this format and the corresponding string is generated as output. Time format should be (number:number:number) and If the time is not in this format, the output will be received as an Invalid date.

```
<script> 
// Here some different values has been 
// assigned while creating Date object 
var dateobj1 = new Date('1'); 
var dateobj2 = new Date('2, 3'); 
var dateobj3 = new Date('4, 5, 6'); 
var dateobj4 = new Date('7, 8, 3, 4'); 
var dateobj5 = new Date('4, 5, 6, 11:00:12'); 
var dateobj6 = new Date('12, 5, 4, 0:0'); 
  
// Contents of above date objects is converted 
// into strings using toString() function. 
var B = dateobj1.toString(); 
var C = dateobj2.toString(); 
var D = dateobj3.toString(); 
var E = dateobj4.toString(); 
var F = dateobj5.toString(); 
var G = dateobj6.toString(); 
  
// Printing the converted string. 
document.write(B + "<br>"); 
document.write(C + "<br>"); 
document.write(D + "<br>"); 
document.write(E + "<br>"); 
document.write(F + "<br>"); 
document.write(G); 
</script> 
```

Output:

```
Mon Jan 01 2001 00:00:00 GMT+0530 (India Standard Time)
Sat Feb 03 2001 00:00:00 GMT+0530 (India Standard Time)
Wed Apr 05 2006 00:00:00 GMT+0530 (India Standard Time)
Invalid Date"
Wed Apr 05 2006 11:00:12 GMT+0530 (India Standard Time)
Sun Dec 05 2004 00:00:00 GMT+0530 (India Standard Time)
```

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari