---
image: "/assets/default-social-image.png"
title: JavaScript date.setMilliseconds() function
categories: JavaScript-date
---

The date.setMilliseconds() is a built-in function in JavaScript that is used to set milliseconds into a date object that is generated using the constructor date().

Syntax:

`dateObj.setMilliseconds(milliseconds_Value);`

DateObj is a valid Date object generated using the Date) (constructor where we want the millisecond to be set. The Millisecond value ranges between 0 and 999.

**Parameter:**

The parameter here is milliseconds_Value, i.e., the millisecond value that is used to set in date() constructor.

**Return Values:**

It returns the new modified millisecond that is set by the function setMilliseconds().

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 13, 1996 05:35:32:77'); 
  
// new millisecond of 52 is being set in above Date 
// Object with the help of setMilliseconds() function 
dateobj.setMilliseconds(52); 
  
// new millisecond from above Date Object is 
// being extracted using getMilliseconds() 
var B = dateobj.getMilliseconds(); 
  
// Printing new millisecond 
document.write(B); 
</script> 
```

Output:

`52`

**Errors and Exceptions**

Example 1:

If we don't offer milliseconds in Date() constructor, then setMilliseconds() can set new milliseconds which will be provided as its parameter.

```
<script> 
// Here millisecond has not been assigned 
// while creating Date object 
var dateobj = new Date('October 13, 1996'); 
  
// new millisecond of 51 is being set in above Date 
// Object with the help of setMilliseconds() function 
dateobj.setMilliseconds(51); 
  
// new millisecond from above Date Object is 
// being extracted using getMilliseconds() 
var B = dateobj.getMilliseconds(); 
  
// Printing new millisecond 
document.write(B); 
</script> 
```

Output:

`51`

Example 2:

If nothing is given in the Date() constructor as a parameter, then still setMilliseconds() will set millisecond function but month, year, date, etc. will become current ones.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// new millisecond of 42 is being set in above Date 
// Object with the help of setMilliseconds() function 
dateobj.setMilliseconds(42); 
  
// milliseconds from above Date Object is 
// being extracted using getMilliseconds() 
var B = dateobj.getMilliseconds(); 
  
// month from above Date Object is 
// being extracted using getMonth() 
var C = dateobj.getMonth(); 
  
// date from above Date Object is 
// being extracted using getDate() 
var D = dateobj.getDate(); 
  
// year from above Date Object is 
// being extracted using getFullYear() 
var E = dateobj.getFullYear(); 
  
// Printing new milliseconds 
document.write(B + "<br>"); 
  
// Printing current month 
document.write(C + "<br>"); 
  
// Printing current date 
document.write(D + "<br>"); 
  
// Printing current year 
document.write(E); 
</script> 
```

Output:

```
42
4
1
2018
```

The 42 here is the new milliseconds, 4 is the current month i.e. April, 1 is the current date and 2018 is the current year.

Example 3:

If the value of millisecond 1006 is given as the setMilliseconds() function parameter, it will set 6 as the millisecond because the millisecond range is between 0 and 999 and therefore between 1006-1000=6, here 1000 is removed as between 0 and 999 is 1000.

```
<script> 
// Here date has been assigned 
// while creating Date object 
var dateobj = new Date('October 13, 1996 05:35:32:45'); 
  
// new millisecond of 1006 is being set in above Date 
// Object with the help of setMilliseconds() function 
dateobj.setMilliseconds(1006); 
  
// milliseconds from above Date Object is 
// being extracted using getMilliseconds() 
var B = dateobj.getMilliseconds(); 
  
// Second from above Date Object is 
// being extracted using getSeconds() 
var C = dateobj.getSeconds(); 
  
// Printing new Milliseconds 
document.write(B + "<br>"); 
  
// Printing second 
document.write(C); 
</script> 
```

Output:

```
6
33
```

Here 6 is the new millisecond and the second is 33 from 32 because the millisecond scale is from 0 to 999 i.e. a total of 1000 so we set new milliseconds as 1006 which increase second by one from 32 to 33 and millisecond by 6.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari