---
image: "/assets/default-social-image.png"
title: JavaScript Math.trunc() Function
categories: JavaScript-math
---

The Math.trunc() method in JavaScript is used for eliminating the fractional digits to retrieve the integer portion of a floating-point number. In other terms, the function Math.trunc() breaks the dot and all the digits to its right.

**Syntax:**

`Math.trunc(value)`

**Parameters:**

This function recognizes a value of single parameter. It is the floating-point number that must be sent to the Math.trunc().

**Return Value:**

The method Math.trunc() returns the integer part of the provided number.

Example 1:

If passing the parameter as a positive number of float type:

```
<script type="text/javascript"> 
   document.write(Math.trunc(15.56));          
</script> 
```

Output:

`15`

Example 2:

If passing the parameter as a negative number of float type:

```
<script type="text/javascript"> 
   document.write(Math.trunc(-15.56));          
</script> 
```

Output:

`-15`

Example 3:

If passing the parameter as a positive number between 0 to 1:

```
<script type="text/javascript"> 
   document.write(Math.trunc(0.236));          
</script> 
```

Output:

`0`

Example 4:

If passing the parameter as a negative number between 0 to 1:

```
<script type="text/javascript"> 
   document.write(Math.trunc(-0.236));          
</script> 
```

Output:

`0`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari