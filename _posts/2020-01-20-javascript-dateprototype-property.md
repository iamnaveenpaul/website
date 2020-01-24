---
image: "/assets/default-social-image.png"
title: JavaScript Date.prototype property
categories: JavaScript-date
---

The Date.prototype property reflects the Date Constructor prototype.

The methods are as follows:

* **getDate():** This process returns the day of the month by local time for the given date.
* **getDay():** This process returns the day of the week (0 for Sunday and 6 for Saturday) according to the local time for the given date.
* **getFullYear():** This returns the year according to local time, for the given date.
* **getHours():** This returns hour(0-23) by local time for the given date.
* **getMilliseconds:** This returns the milliseconds (0-999) according to local time for the given date.
* **getMinutes():** This returns the minutes (0-59) by local time for the given date.
* **getMonth():** This returns a month (0-11) by local time for the given date.
* **getSeconds():** This returns the seconds (0-59) by local time for the given date.
* **getTime():** This shows the number of ellapsed milliseconds after January 01, 1970 00:00:00 UTC. The period before the specified time is negative.
* **getTimeozneOffset():** For current location, this returns the timezone offset in minutes.
* **getUTCDate():** This returns the date of the month (1-31) according to universal time for the given date.
* **getUTCDay():** This returns the day of the week (0-6) according to universal time for the given date.
* **getUTCFullYear():** This returns the year by universal time for the date mentioned.
* **getUTCHours():** This returns the hours (0-23) by universal time for the date stated.
* **getUTCMilliseconds():** This returns the milliseconds (0-999) by universal time for the given date.
* **getUTCMinutes():** This returns the minutes (0-59) according to universal time for the given date.
* **getUTCMonth():** This returns the month (0-11) by universal time for the date indicated.
* **getUTCSeconds():** This returns the seconds (0-59) by universal time for the date defined.

Example:

```
<script> 
    
  var birthday = new Date('June 21, 2018 16:44:23'); 
  var date1 = birthday.getDate();  
  var day1 = birthday.getDay();  
  var year1 = birthday.getFullYear();  
  var hour1 = birthday.getHours();  
  var ms1 = birthday.getMilliseconds();  
  var m1 = birthday.getMinutes();  
  var mth1 = birthday.getMonth();  
  var time1 = birthday.getTime();  
  var s1 = birthday.getSeconds();  
  var offset = birthday.getTimezoneOffset();  
  var date2 = birthday.getUTCDate();  
  var day2 = birthday.getUTCDay();  
  var year2 = birthday.getUTCFullYear();  
  var hour2 = birthday.getUTCHours();  
  var ms2 = birthday.getUTCMilliseconds(); 
  var um1 = birthday.getUTCMinutes(); 
  var umth = birthday.getUTCMonth(); 
  var us = birthday.getUTCSeconds(); 
  
  document.write(date1 +"<br>"); 
  
  document.write(day1 +"<br>"); 
  
  document.write(year1 +"<br>"); 
  
  document.write(hour1 +"<br>"); 
  
  document.write(ms1 +"<br>"); 
  
  document.write(m1 +"<br>"); 
  
  document.write(mth1 +"<br>"); 
  
  document.write(time1 +"<br>"); 
  
  document.write(s1 +"<br>"); 
  
  document.write(offset +"<br>"); 
  
  document.write(date2 +"<br>"); 
  
  document.write(day2 +"<br>"); 
  
  document.write(year2 +"<br>"); 
  
  document.write(hour2 +"<br>"); 
  
  document.write(ms2 +"<br>"); 
  
  document.write(um1 +"<br>"); 
  
  document.write(umth +"<br>"); 
  
  document.write(us);         
</script> 
```

Output:

```
21
4
2018
16
0
44
5
1529579663000
23
-330
21
4
2018
11
0
14
5
23
```

This also has some certain approaches that can be used to convert the date into various formats:

* **toDateString():** Returns a human readable string of the "date" portion of the Date.
* **toGMTString():** Returns a string of the date based on the time zone of the GMT (UT).
* **toLocaleFormat():** Converts a date to a string using a format string.
* **toLocalestring():** Returns a string with this date representation sensitive to locality.
* **toString():** Returns a string representing the given object Date.
* **toTimeString():** Returns a human readable string of the "time" portion of the Date.
* **valueOf():** Returns the basic attribute of an object Time.

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari