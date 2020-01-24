---
image: "/assets/default-social-image.png"
title: JavaScript date.getMonth() method
categories: JavaScript-date
---

The date.getMonth() is a built-in JavaScript function that is used to retrieve the month from the provided Date object.

**Syntax:**

`DateObj.getMonth()`

In the above syntax, DateObj is a valid Date object generated with the use of Date() conctructor from which we would like to get months.

**Parameter:**

This function takes no parameters. This is only used in combination with a date object that we want to collect months from.

**Return Value:**

It returns the month for the object specified in Month. The month is a value of 0 to 11 for an integer. Zero (0) means January, 1 means February and so on until December as 11.

Example 1:

```
<script type="text/javascript"> 
  
// creating a Date Object 
var DateObj = new Date('October 15, 1996 05:35:32'); 
  
// month from above Date Object is 
// being extracted using getMonth() 
var months = DateObj.getMonth(); 
  
// Printing month. 
document.write(months); 
  
</script> 
```

Output:

`9`

**Errors and Exceptions:**

Example 1:

Here the month's date should be between 1 and 31 because no date can be more than 31 dates. That's why, if the month in the Date object is greater than 31, it returns NaN i.e., Not a number.

```
<script type="text/javascript"> 
  
// Creating a Date Object 
var DateObj = new Date('October 33, 1996 05:35:32'); 
  
// month from above Date Object is being  
// extracted using getMonth() 
var months = DateObj.getMonth(); 
  
// Printing month. 
document.write(months); 
  
</script> 
```

Output:

`NaN`

Example 2:

If no month is given, this returns zero (0).

```
<script type="text/javascript"> 
  
// Creating a Date Object 
var DateObj = new Date('1996 05:35:32'); 
  
// month from above Date Object is being  
// extracted using getMonth() 
var months = DateObj.getMonth(); 
  
// Printing month. 
document.write(months); 
  
</script> 
```

Output:

`0`

Example 3:

If nothing is given as parameter, the current month will be returned.

```
<script type="text/javascript"> 
  
// Creating a Date Object 
var DateObj = new Date(); 
  
// month from above Date Object is being  
// extracted using getMonth() 
var months = DateObj.getMonth(); 
  
// Printing month. 
document.write(months); 
  
</script> 
```

Output:

`2`

**Application:**

It's got lots of applications including receiving the current month. The program below demonstrates one of that function's implementations. It brings the month that is the current.

Example 1:

```
<script type="text/javascript"> 
  
// Creating a Date Object 
var DateObj = new Date(); 
  
// month from above Date Object is being  
// extracted using getMonth() 
var months = DateObj.getMonth(); 
  
// Printing month. 
document.write(months); 
  
</script> 
```

Output:

`2`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari