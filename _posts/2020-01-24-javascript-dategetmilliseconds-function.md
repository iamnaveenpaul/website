---
image: "/assets/default-social-image.png"
title: JavaScript date.getMilliseconds() Function
categories: JavaScript-date
---

The date.getMilliseconds() is a built-in JavaScript function that is used to retrieve the milliseconds from a specified Date object.

**Syntax:**

`DateObj.getMilliseconds()`

In the above notation, the DateObj is a valid Date object generated using Date() conctructor from which milliseconds are to be taken.

**Parameter:**

This function takes no parameters. It's just used in conjunction with a date object that we want to get milliseconds from.

**Return values:**

For the specified date value, it returns the millisecond, a number between 0 and 999.

Example 1:

```
<script> 
  // Here a date has been assigned 
  // while creating Date object 
  var DateObj = new Date('October 15, 1996 05:35:32:77'); 
  
  // millisecond from above date object is 
  // being extracted using getMilliseconds(). 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing millisecond 
  document.write(millisec); 
</script> 
```

Output:

`77`

Errors and Exceptions:

Example 1:

The month's value should be from 1 and 31 because none of the month has a date greater than 31, which is why it returns NaN i.e. not a number because there is no date for the month.

```
<script> 
  // Here a date has been assigned 
  // while creating Date object 
  var DateObj = new Date('October 33, 1996 05:35:32:77'); 
  
  // millisecond from above dateobject is 
  // being extracted using getMilliseconds(). 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing millisecond 
  document.write(millisec); 
</script> 
```

Output:

`NaN`

Example 2:

When milliseconds are not given instead, output will be zero(0).

```
<script> 
  // Here a date has been assigned 
  // while creating Date object 
  var DateObj = new Date('October 13, 1996 05:35:32'); 
  
  // millisecond from above dateobject is being 
  // extracted using getMilliseconds() 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing millisecond 
  document.write(millisec); 
</script> 
```

Output:

`0`

Example 3:

If nothing is provided to the Date() constructor as a parameter, the current millisecond will be returned.

```
<script> 
  // Creating a Date Object 
  var DateObj = new Date(); 
  
  // millisecond from above Date object is being 
  // extracted using getMilliSeconds() 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing current millisecond 
  document.write(millisec); 
</script> 
```

Output:

`279`

Example 4:

When generating the Date object, milliseconds as 1003 is given, the method returns 0 as an exception because the number of milliseconds between 0 and 999 and 1003 is out of the range.

```
<script> 
  // Here a date has been assigned 
  // while creating Date object 
  var DateObj = new Date('October 13, 1996 05:35:32:1003'); 
  
  // millisecond from above dateobject is being 
  // extracted using getMilliseconds() 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing millisecond 
  document.write(millisec); 
</script> 
```

Output:

`0`

**Application:**

It's got a lot of applications like getting the current millisecond. The program below demonstrates one of that function's implementations. Which offers millisecond as the current value.

Example 1:

```
<script> 
  // Creating Date Object 
  var DateObj = new Date(); 
  
  // millisecond from above Date Obect is 
  // being extracted using getMilliSeconds() 
  var millisec = DateObj.getMilliseconds(); 
  
  // Printing current millisecond 
  document.write(millisec); 
</script> 
```

Output:

`79`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari