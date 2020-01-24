---
image: "/assets/default-social-image.png"
title: JavaScript date.toTimeString() function
categories: JavaScript-date
---

The date.toTimeString() is a JavaScript built-in function used to return the time component of the specified date object in english. The date object is generated using the date() constructor.

**Syntax:**

`dateObj.toTimeString()`

Note: For the above, DateObj is a valid Date object created using Date() constructor, the content of which is returned in the time portion.

**Parameters:**

This function requires no parameters. It is only used in combination with an object generated using Date() constructor whose contents of the time portion are returned in English as the language

**Return Values:**

It returns in English, the time portion of the specified date object.

```
<script> 
  
// Here a date has been assigned 
// while creating Date object 
var dateobj = new Date('October 15, 1996 05:35:32'); 
  
// Contents of above date object 
// of time portion is returned 
// using toTimeString() function. 
var B = dateobj.toTimeString(); 
  
// Printing the time. 
document.write(B); 
</script> 
```

Output:

`05:35:32 GMT+0530 (India Standard Time)`

**Errors and Exceptional cases**

Nothing is provided here as a parameter when constructing the date object but it still returns the current time to TimeString() function.

```
<script> 
// Here nothing has been assigned 
// while creating Date object 
var dateobj = new Date(); 
  
// It return current time using  
// toTimeString() function. 
var B = dateobj.toTimeString(); 
  
// Printing the current time. 
document.write(B); 
</script> 
```

Output:

`14:58:08 GMT+0530 (India Standard Time)`

If time component is not supplied to the Date() constructor as the parameter, then it will return the time in zeros(0) value.

```
<script> 
// Only month date and year are  
// assigned without time while 
// creating Date object. 
var dateobj = new Date('October 15, 1996'); 
  
// It returns time using  
// toTimeString() function. 
var B = dateobj.toTimeString(); 
  
// Printing the time. 
document.write(B); 
</script> 
```

Output:

`00:00:00 GMT+0530 (India Standard Time)`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari