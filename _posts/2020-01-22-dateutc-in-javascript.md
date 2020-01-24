---
image: "/assets/default-social-image.png"
title: Date.UTC() In JavaScript
categories: JavaScript-date
---

The JavaScript Date.UTC() function is used to calculate the amount of milliseconds in a Date object as from January 1, 1970, 00:00:00, universal time.

The method UTC() varies in two respects from Date constructor:

Date.UTC() instead of local time, uses universal time.

Date.UTC() returns the time value as a number, rather than constructing an object Date.

**Syntax:**

```
Date.UTC(year, month[, day[, hour[, minute[, second[, millisecond]]]]])
```

**Parameters:**

**year:** A year after 1900 to be specified.

**month:** To specify an integer value representing the month between 0 and 11. Other values that are authorized are:

* -1, the last month of the previous year to be represented.
* 12 will be the first month of the following year.
* 13 will be the second month of the following year.

**day:** The parameter is optional and is used to define an integer number between 1 and 31 which represents the month's day. Further allowed values are:

* 0 will be the last hour of the prior month.
* -1 is the hour before the last hour of the prior month.
* If the month has 31 days, 32 will represent the next month's first day.
* If the month has 30 days, the next month's second day will be 32.

**hour:** The value is optional and is used to define an integer value representing the hours between 0 and 23. Further allowed values are:

* -1 will serve the last hour of the prior day.
* 24 will serve the next day's first hour.

**minute:** The parameter is optional and is used to define an integer value between 0 and 59 representing the minutes. Other permitted values are:

-1,  the last minute of the previous hour to be represented.
60 will reflect the next hour's first minute.

**second:** It is the optional parameter and is used to define an integer value representing seconds between 0 and 59. Some acceptable values are:

-1 is the last second of the previous minute.
60 is the first second of the precceding minute.

**millisecond:** The parameter is optional and is used to define an integer value describing the milliseconds between 0 and 999. Other values that are permitted are:

-1 is the last millisecond of the preceding second.
1000 is the first millisecond of next second.

**Return value:**

The Date.UTC() method returns an amount representing the number of milliseconds since January 1, 1970, 00:00:00, universal time, in the given Date object.

Example 1:

```
Input : Date.UTC(2010, 01, 28)
Output : 1267315200000
```

In this case, three parameters are passed in the Date.UTC() function reflecting year, month and day separately. The method returns the amount of milliseconds between the date as parameter and the midnight of January 1, 1970.

Example 2:

```
Input : new Date(Date.UTC(2010, 01, 28))
Output : Sun Feb 28 2010 05:30:00 GMT+0530 (IST)
```

In this case, the Date.UTC() function passes three parameters representing year, month and day separately and generates a date object "new date." The function returns the UTC time for the parameters passed.

Example 1:

```
<script> 
var test = Date.UTC(2010, 01, 28); 
document.write("OUTPUT : " + test); 
</script> 
```

OUTPUT:

`OUTPUT : 1267315200000`

The amount of milliseconds between a mentioned date and midnight January 1 1970 is returned in this method.

Example 2:
        
```
<script> 
var test = new Date(Date.UTC(2010, 01, 28)); 
document.write("OUTPUT : " + test); 
</script> 
```

OUTPUT:

`OUTPUT : Sun Feb 28 2010 05:30:00 GMT+0530 (IST)`

In this, a date object is generated using UTC time instead of local time.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari