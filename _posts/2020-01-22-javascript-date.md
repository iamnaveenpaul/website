---
image: "/assets/default-social-image.png"
title: JavaScript Date
categories: JavaScript-date
---

The JavaScript Date object is used for describing a moment of time. This time value is the UTC (Coordinated Universal Time) and is since 1 January 1970. With the Date object, we may construct a date by calling the new Date() constructor as shown in the syntax below.

**Syntax:**

```
new Date();
new Date(value);
new Date(dateString);
new Date(year, month, day, hours, minutes, seconds, milliseconds);
```

**Parameters:**

* **value:** This value is millisecond number after 1 January 1970, 00:00:00 UTC.
* **dateString:** That is a date format.
* **year:** This is expressed by numerical values varying between the years 1900 and 1999.
* **month:** This is defined by integer values ranging from January as 0 to December as 11.
* **day:** This parameter is an optional. For the day of the month, this is represented by integer value.
* **hours:** This is optional and for the hour of the day, this is expressed by an integer value.
* **minutes:** This is optional and for the minute of a time, this is represented by the integer value.
* **seconds:** This is optional and for the second of a time, this is expressed by the integer value.
* **milliseconds:** This is optional and for the millisecond of a time, this is expressed by integer value.

**Return Values:**

If nothing is given as the parameter, this returns the current date and time otherwise it returns the date format and time in which parameter is specified.

Example 1:

If nothing is given as the parameter, it returns the date and time of the moment.

```
<script> 
  // If nothing as parameter is given,  
  // it represent the present date and time. 
  var A = new Date(); 
  
  // Printing present date and time. 
  document.write(A); 
</script> 
```

Output:

`Wed Mar 21 2018 20:44:40 GMT+0530 (India Standard Time)`

Example 2:

If any integer value is taken as the parameter, then the amount of milliseconds provided since January 1, 1970, 00:00:00 UTC is given.

```
<script> 
  // Parameter as integer value give the number of  
  // milliseconds since January 1, 1970, 00:00:00 UTC. 
  var A = new Date(32549); 
  
  document.write(A); 
</script> 
```

Output:

`Thu Jan 01 1970 05:30:32 GMT+0530 (India Standard Time)`

Example 3:

If any dataString is given as the parameter, then this returns the same as the parameter including the name of the day.

```
<script> 
  // When any dataString is given as the parameter  
  // then it return the same as the parameter 
  // including day name. 
  var A = new Date('June 22, 1985 07:19:35'); 
  
  document.write(A); 
</script> 
```

Output:

`Sat Jun 22 1985 07:19:35 GMT+0530 (India Standard Time)`

Example 4:

When certain numbers are taken as the parameter, then they are respectively considered as year, month, day, hours, minutes, seconds, milliseconds.

```
<script> 
  // When some numbers are taken as the parameter  
  // then they are considered as year, month, day,  
  // hours, minutes, seconds, milliseconds  
  // respectively. 
  var A = new Date(1996, 10, 13, 5, 30, 22); 
  
  document.write(A); 
</script> 
```

Output:

`Wed Nov 13 1996 05:30:22 GMT+0530 (India Standard Time)`

**Errors and Exceptions:**

You need to check in console to check this out.

Example 1:

Any integer number should be taken, as there is no name to the parameter, otherwise it throws an error.

```
<script> 
  // Any integer number should be taken  
  // as the parameter not any name. 
  var A = new Date(gfg); 
  
  document.write(A); 
</script> 
```

Output:

`Error: gfg is not defined`

Example 2:

Any integer amount should be taken as no other number e.g. complex number to be taken as the parameter.

```
<script> 
  // Any integer number should be take as  
  // the parameter not any other number 
  // e.g- complex number. 
  var A = new Date(1 + 5i); 
  
  document.write(A); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

Any integer number should be considered as no other number, e.g. complex number, to be the parameter.

```
<script> 
  // Any integer number should be taken 
  //  as the dateString not word. 
  var A = new Date("geeksforgeeks"); 
  
  document.write(A); 
</script> 
```

Output:

`Invalid Date`

**Application:**

It has several applications, like getting the exact date and time of the current. The program below prints the actual date and time using the object Date().

```
<script> 
  // If nothing as parameter is given, it  
  // represent the present date and time. 
  var A = new Date(); 
  
  // Printing present date and time. 
  document.write(A); 
</script> 
```

Output:

`Wed Mar 21 2018 20:44:40 GMT+0530 (India Standard Time)`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari