---
image: "/assets/default-social-image.png"
title: JavaScript date.toDateString() function
categories: JavaScript-date
---

The date.toDateString() is a JavaScript built-in function which is used to transform the date component contents of the provided date object into a string. The date object is generated using the date() constructor. DateObj is a valid Date object generated using the constructor Date() whose date section content is translated to string, for the syntax.

**Syntax:**

`dateObj.toDateString()`

**Parameters:**

There is no parameter needed for this function. This is only used in conjunction with an object that was created using the constructor Date().

**Return Values:**

returns the transformed string from the date component of the Date() constructor content.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 15, 1996 05:35:32'); 
  
// Contents of date portion of above date object 
// is converted into a string using toDateString() function. 
var B = dateobj.toDateString(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`Tue Oct 15 1996`

**Errors and Exceptions**

Example 1:

Nothing is passed here as parameter when generating date object but it still returns the current day name, month name, date, year to DateString() function.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// Contents of date portion of above date object is 
// converted into a string using toDateString() function. 
var B = dateobj.toDateString(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`Mon Apr 23 2018`

Example 2:

If some random list of values is passed, then return the corresponding string to DateString() function.

The Date() Constructor format is similar to Date(month, date, year, time). In the program below, some values are given by using this format and the corresponding string is generated as output. It should be as time format (number:number:number). If time in this format does not lie, it will give output as Invalid date.

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
  
// Contents of date portion of above date objects is 
// converted into strings using toDateString() function. 
var B = dateobj1.toDateString(); 
var C = dateobj2.toDateString(); 
var D = dateobj3.toDateString(); 
var E = dateobj4.toDateString(); 
var F = dateobj5.toDateString(); 
var G = dateobj6.toDateString(); 
  
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
Mon Jan 01 2001
Sat Feb 03 2001
Wed Apr 05 2006
Invalid Date
Wed Apr 05 2006
Sun Dec 05 2004
```

Note:

Months, date, hour, minute, second and millisecond should be between 0 and 11 for months, between 1 and 31 for day, between 0 and 23 for hours, between 0 and 59 for minute, between 0 and 59 for seconds, between 0 and 999 milliseconds, or else toDateString() returns invalid date

Example 1:

Here date given as of 45, which is out of date range, which is why the output as null as shown below.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 45, 1996 05:35:32'); 
  
// Contents of date portion of above date object is 
// converted into a string using toDateString() function. 
var B = dateobj.toDateString(); 
  
// Printing the converted string. 
document.write(B); 
</script> 
```

Output:

`Invalid Date`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari