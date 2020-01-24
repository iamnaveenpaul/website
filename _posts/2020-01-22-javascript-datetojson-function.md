---
image: "/assets/default-social-image.png"
title: JavaScript date.toJSON() function
categories: JavaScript-date
---

The date.toJSON() is a built-in function in JavaScript that is used to transform the contents of the specified date object into a string. The date object is created using the constructor date().

In the syntax below, DateObj is a valid Date object created using the constructor Date() of which the contents are converted to string.

**Syntax:**

`dateObj.toJSON()`

**Parameters:**

This function requires no parameters. It is only used in combination with an object that was generated using Date() conctructor.

**Return Value:**

This returns the converted string of contents of the Date() constructor.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 15, 1996 05:35:32'); 
  
// Contents of above date object is converted 
// into a string using toJSON() function. 
var B = dateobj.toJSON(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`1996-10-15T00:05:32.000Z`

**Errors and Exceptions**

Example 1:

Nothing is passed as a parameter here while generating date object yet still returning the current day name, month name, year, year and time to JSON() method.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// Contents of above date object is 
// converted into a string using toJSON() function. 
var B = dateobj.toJSON(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`2018-04-23T11:24:14.955Z`

Example 2:

When passing any random value set, toJSON() function returns the corresponding string.

The Date() constructor format is similar to Date(month, date, year, tim). In the program below some values are given by following this format and the subsequent string is generated as output. It would be as time format (number:number:number).

```
<script> 
// Here some different values has been 
// assigned while creating Date object 
var dateobj1 = new Date('1'); 
var dateobj2 = new Date('2, 3'); 
var dateobj3 = new Date('4, 5, 6'); 
var dateobj4 = new Date('4, 5, 6, 11:00:12'); 
var dateobj5 = new Date('12, 5, 4, 0:0'); 
  
// Contents of above date objects is converted 
// into strings using toJSON() function. 
var B = dateobj1.toJSON(); 
var C = dateobj2.toJSON(); 
var D = dateobj3.toJSON(); 
var E = dateobj4.toJSON(); 
var F = dateobj5.toJSON(); 
  
// Printing the converted string. 
document.write(B + "<br>"); 
document.write(C + "<br>"); 
document.write(D + "<br>"); 
document.write(E + "<br>"); 
document.write(F); 
</script> 
```

Output:

```
2000-12-31T18:30:00.000Z
2001-02-02T18:30:00.000Z
2006-04-04T18:30:00.000Z
2006-04-05T05:30:12.000Z
2004-12-04T18:30:00.000Z
```

**Important Points**

Months, date, hour, minute, second and millisecond must be between 0 and 11 for months, between 1 and 31 for date, between 0 and 23 for hours, between 0 and 59 for minutes and seconds and between 0 to 999 for milliseconds otherwise null is returned to JSON().

Here date mentioned as of 45 and that is out of date range, which is why the output as null is presented below in the code.

```
<script> 
// Here a date has been assigned 
// while creating a Date object 
var dateobj = new Date('October 45, 1996 05:35:32'); 
  
// Contents of above date object is converted 
// into a string using toJSON() function. 
var B = dateobj.toJSON(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`null`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari