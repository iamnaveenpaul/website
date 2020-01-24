---
image: "/assets/default-social-image.png"
title: JavaScript date.setMonth() function
categories: JavaScript-date
---

The date.setMonth() is a JavaScript built-in function that is used to set month into a date object that is generated using the Date() constructor.

**Syntax:**

`DateObj.setMonth(month_Value);`

DateObj is a valid Date object generated using Date() constructor in which we want to set the month. Month value is from 0 to 11 because the cumulative number of months in a year is 12, from January to December. Value 0 is used for January, 1 for February and so on until December as 11.

**Parameter:**

The month_Value parameter here is the month value that we want to place in the week that was generated using the Week() constructor.

**Return Values:**

It returns the new i.e. updated month which is defined by the function setMonth().

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 13, 1996 05:35:32'); 
  
// new month of January is being set in above Date 
// Object with the help of setMonth() function 
dateobj.setMonth(0); 
  
// new month from above Date Object is 
// being extracted using getMonth() 
var B = dateobj.getMonth(); 
  
// Printing new month 
document.write(B); 
</script> 
```

Output:

`0`

**Errors and Exceptions**

Example 1:

If we don't send any month when constructing the date object in Date() constructor, setMonth() will still be able to set new month in the created date object.

```
<script> 
// Here month has not been assigned 
// while creating Date object 
var dateobj = new Date('1996, 05:35:32'); 
  
// new month of 2 is being set in above Date 
// Object with the help of setMonth() function 
dateobj.setMonth(2); 
  
// new month from above Date Object is 
// being extracted using getMonth() 
var B = dateobj.getMonth(); 
  
// Printing new month 
document.write(B); 
</script> 
```

Output:

`2`

Example 2:

If nothing is provided as a parameter in the constructor Date(), the function setMonth() will be able to set month but year, date etc. remains current.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// new month of 11 is being set in above Date 
// Object with the help of setMonth() function 
dateobj.setMonth(11); 
  
// Month from above Date Object is 
// being extracted using getMonth() 
var B = dateobj.getMonth(); 
  
// date from above Date Object is 
// being extracted using getDate() 
var C = dateobj.getDate(); 
  
// year from above Date Object is 
// being extracted using getFullYear() 
var D = dateobj.getFullYear(); 
  
// Printing new month 
document.write(B + "<br>"); 
  
// Printing current date 
document.write(C + "<br>"); 
  
// Printing current year 
document.write(D); 
</script> 
```

Output:

```
11
1
2018
```

The new month of December is here 11, the current date is 1 and the current year is 2018.

Example 3:

If the value of the month 15 is given as the setMonth() function parameter, it will set 3 as the month because the range of the month is from 0 to 11 and therefore (15%12 = 3).

```
<script> 
// Here date has been assigned 
// while creating Date object 
var dateobj = new Date('October 13, 1996 05:35:32'); 
  
// new month of 15 is being set in above Date 
// Object with the help of setMonth() function 
dateobj.setMonth(15); 
  
// month from above Date Object is 
// being extracted using getMonth() 
var B = dateobj.getMonth(); 
  
// year from above Date Object is 
// being extracted using getFullYear() 
var C = dateobj.getFullYear(); 
  
// Printing new month 
document.write(B + "<br>"); 
  
// Printing new year 
document.write(C); 
</script> 
```

Output:

Here 3 is the new month of April and year from 1996 is 1997 as month range is from 0 to 11 i.e. a total of 12 and we set new month as 3 and rises year by year from 1996 to 1997 and month is 3.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari