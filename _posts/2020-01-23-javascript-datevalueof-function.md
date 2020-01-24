---
image: "/assets/default-social-image.png"
title: JavaScript date.valueOf() function
categories: JavaScript-date
---

The date.valueOf() is a built-in function in JavaScript that is used for value between 1 January 1970 00:00:00 UTC and the specified date to get the number of milliseconds.

**Syntax:**

`dateObj.valueOf()`

Note: From the above notation, DateObj is a valid date object generated using Date() constructor whose content is used to get the number of milliseconds between 1 January 1970 00:00:00 UTC and the date specified as the Date() constructor's value.

**Parameters:**

The function requires no parameter. This is only used in combination with an object Date generated using the constructor Date().

**Return Values:**

It returns the number of milliseconds as the Date() constructor contents between 1 January 1970 00:00:00 UTC and the date specified.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 15, 1996 05:35:32'); 
  
// Getting the number of milliseconds between  
//1 January 1970 00:00:00 
// UTC and the given date as the content of  
//the above Date() constructor. 
var B = dateobj.valueOf(); 
  
// Printing the calculated number of milliseconds. 
document.write(B); 
</script> 
```

Output:

`845337932000`

**Errors and Exceptions**

If nothing is provided as a parameter when generating the date object but still valueOf() function returns the millisecond amount between January 1, 1970 00:00:00 UTC and the current time.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// Getting the number of milliseconds between  
//1 January 1970 00:00:00 
// UTC and the current date. 
var B = dateobj.valueOf(); 
  
// Printing the calculated number of milliseconds. 
document.write(B); 
</script> 
```

Output:

`1524387231290`

A month's date varying from 1 to 31. If the date is taken out of date range like 35, that returns NaN i.e. not a number.

```
<script> 
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 35, 1996 05:35:32'); 
  
// Getting the number of milliseconds between  
//1 January 1970 00:00:00 
// UTC and the given date. 
var B = dateobj.valueOf(); 
  
// Printing the calculated number of milliseconds. 
document.write(B); 
</script> 
```

Output:

`NaN`

Note: Months, dates, hours, minutes, seconds, milliseconds should all be within their respective scope. If not, valueOf() returns NaN, not a number. Range of months, days, hours, minutes, seconds, milliseconds are 0-11, 1-31, 0-23, 0-59, 0-59, 0-999 respectively.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari