---
image: "/assets/default-social-image.png"
title: JavaScript Date.parse()
categories: JavaScript-functions
---

The Date.parse() function is a built-in JavaScript function that allows us to know the exact amount of milliseconds elapsed after midnight, January 1, 1970, until the date we give.

**Syntax:**

`Date.parse(datestring);`

Parameters: This method takes a datestring parameter that is received as the input.

Return Values: returns an integer value reflecting the millisecond number between January 1, 1970, midnight, and the date given. If the computer can not identify the string by any way or the input string is invalid, instead of an integer, it will return "NaN."

Code to show the working of Date.parse() function:

Example 1:

```
<script> 
  
    // Taking a date string as input. 
    var date = "February 18, 2018 12:30 PM"; 
      
    // Calling parse function on input date string. 
    var msec = Date.parse(date); 
    document.write(msec); 
      
</script> 
```

Output:

`1518937200000`

Example 2:

If the date input string is not right, not a number, ie, NaN will be returned.

```
<script> 
  
    // Taking wrong date string as input. 
    var date = "February 48, 2018 12:30 PM"; 
      
    // calling parse function. 
    var msec = Date.parse(date); 
    document.write(msec); 
      
</script> 
```

Output:

`NaN`

**Why 01 Jan 1970 00:00:00 GMT?**

It is called the time of Unix, i.e. the time of invention of Unix. This is used by nearly all programming languages, and operating systems as their starting time reference.

Note: Once we have the millisecond count for two periods, through simple math approximation we can quickly find the number of hours, days, months, years, etc.

Supported browsers: JavaScript Date.parse() supported browsers are described as follows:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari