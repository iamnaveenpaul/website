---
image: "/assets/default-social-image.png"
title: JavaScript date.setUTCMonth()
categories: JavaScript-date
---

The date.setUTCMonth() is a built-in function in JavaScript that is used to set month to a date object that is formed using the date() constructor as per universal time.

**Syntax:**

`dateObj.setUTCMonth(month_Value);`

DateObj is a valid Date object created with the Date() constructor in which the month is set. Month value ranges from 0 to 11, since the total number of months in a year is 12 from January to December. Value 0 is used for January, February as 1 and so forth until December as 11.

**Parameter:**

The parameter here is month_Value, i.e. the month value that is used to set in date() constructor.

**Return values:**

It returns the new i.e. updated month that is set by the function setUTCMonth().

```
<script> 
  
  // Here a date has been assigned according to 
  // universal time while creating Date object 
  var dateobj = new Date('October 13, 1996 05:35:32 GMT-3:00'); 
  
  // new month of January is being set in above Date 
  // Object with the help of setUTCMonth() function 
  dateobj.setUTCMonth(0); 
  
  // new month from above Date Object is 
  // being extracted using getUTCMonth() 
  var B = dateobj.getMonth(); 
  
  // Printing new month 
  document.write(B); 
                         
</script> 
```

Output:

`0`

**Errors and Exceptions**

Example 1:

If we don't provide a month in Date() constructor, then setUTCMonth() will set a new month that will be provided as its parameter.

```
<script> 
  
  // Here month has not been assigned according to 
  // universal time while creating Date object 
  var dateobj = new Date('1996, 05:35:32 GMT-3:00'); 
  
  // new month of 2 is being set in above Date 
  // Object with the help of setUTCMonth() function 
  dateobj.setUTCMonth(2); 
  
  // new month from above Date Object is 
  // being extracted using getUTCMonth() 
  var B = dateobj.getUTCMonth(); 
  
  // Printing new month 
  document.write(B); 
  
</script> 
```

Output:

`2`

Example 2:

If nothing is given in the Date() constructor as a parameter, then still setUTCMonth() will set month but year, date etc will become the actual current as per universal time.

```
<script> 
  
  // Here nothing has been assigned according to 
  // universal time while creating Date object 
  var dateobj = new Date(); 
  
  // new month of 11 is being set in above Date 
  // Object with the help of setUTCMonth() function 
  dateobj.setUTCMonth(11); 
  
  // Month from above Date Object is 
  // being extracted using getUTCMonth() 
  var B = dateobj.getUTCMonth(); 
  
  // date from above Date Object is 
  // being extracted using getUTCDate() 
  var C = dateobj.getUTCDate(); 
  
  // year from above Date Object is 
  // being extracted using getUTCFullYear() 
  var D = dateobj.getUTCFullYear(); 
  
  // Printing new month 
  document.write(B + '<br>'); 
  
  // Printing current date 
  document.write(C + '<br>'); 
  
  // Printing current year 
  document.write(D + '<br>'); 
                          
</script> 
```

Output:

```
11
1
2018
```

Here 11 is December's new month, 1 is the current date and 2018 is the current year as per universal time.

Example 3:

If the value of month 15 is given as the setUTCMonth() function for parameter, it will set 3 as the month because the range of month is from 0 to 11 and therefore 15-12=3, where 12 is subtracted because 0 through 11 is 12.

```
<script> 
  
  // Here date has been assigned according to 
  // universal time while creating Date object 
  var dateobj = new Date('October 13, 1996 05:35:32 GMT-3:00'); 
  
  // new month of 15 is being set in above Date 
  // Object with the help of setUTCMonth() function 
  dateobj.setUTCMonth(15); 
  
  // month from above Date Object is 
  // being extracted using getUTCMonth() 
  var B = dateobj.getUTCMonth(); 
  
  // year from above Date Object is 
  // being extracted using getUTCFullYear() 
  var C = dateobj.getUTCFullYear(); 
  
  // Printing new month 
  document.write(B + '<br>'); 
  
  // Printing new year 
  document.write(C); 
                         
</script> 
```

Output:

```
 3
1997
```

Here 3 is the new month of April and year is 1997 from 1996 since month range is from 0 to 11 i.e. complete 12 and we set new month as 3 that rises year by year from 1996 to 1997 and month is 3 according to universal time.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari