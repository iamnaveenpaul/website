---
image: "/assets/default-social-image.png"
title: JavaScript Date.now()
categories: JavaScript-date
---

The Date.now() is a built-in JavaScript function that returns the milliseconds elapsed since January 1, 1970, 00:00:00 UTC. Since now() is a static Date method, it is always used as Date.now().

Syntax:

`var A = Date.now();`

Where A is time in milliseconds.

**Parameters:**

It doesn't recognize any parameter.

**Return Values:**

It returns the millisecond value that have elapsed since 1 January 1970, 00:00:00 UTC.

Example 1:

```
<script> 
  
  // Use of function Date.now() 
  var A = Date.now(); 
  
  // Printing the number of millisecond elapsed  
  document.write("The time elapsed in millisecond is: " + A); 
  
</script> 
```

Output:

In millisecond time elapsed is: 1529644667834

Example 2:

Use the code below to get the latest date.

```
<script> 
  
  // Use of Date.now() function 
  var d = Date(Date.now()); 
  
  // Converting the number of millisecond in date string 
  a = d.toString() 
  
  // Printing the current date                     
  document.write("The current date is: " + a)  
  
</script> 
```

Output:

`The current date is: Fri Jun 22 2018 10:54:33 GMT+0530 (India Standard Time)`

Example 3:

The Date(Date.now()) is same as Date(), so you can achieve the same result, i.e., the current date by:

```
<script> 
  
  // Using Date() function 
  var d = Date(); 
    
  // Converting the number value to string 
  a = d.toString()  
    
  // Printing the current date 
  document.write("The current date is: " + a) 
    
</script> 
```

Output:

`The current date is: Fri Jun 22 2018 11:02:01 GMT+0530 (India Standard Time)`

**Supported Browsers:**

* Google Chrome
* Internet Explorer 9.0
* Firefox
* Opera
* Safari