---
image: "/assets/default-social-image.png"
title: JavaScript Math.fround() Function
categories: JavaScript-math
---

We may sometimes want to use 32-bit numbers when running operations on numbers. Internally, JavaScript utilizes 64-bit floating point values and not 32-bit ones. It may also fail to check the equality of 32-bit numbers with 64-bit numbers. JavaScript offers us an inbuilt feature to cast a 32-bit 64-bit floating point integer. In JavaScript, the Math.fround() method is used to run to the nearest single-precision 32-bit float expression of a specified number. For JavaScript, the method Math.fround() is also used to convert the 64-bit float to a 32-bit float.

**Syntax:**

`Math.fround(value)`

**Parameters:**

This function acknowledges a value of single parameter. Such parameter refers to the number we want the closest 32-bit single float precision expression to be identified for.

**Return Value:**

The function Math.fround() returns the closest single precision float representation of the given number for 32-bit.

Example 1:

If the passed parameter is a positive number

```
<script type="text/javascript"> 
   document.write(Math.fround(3));           
</script> 
```

Output:

`3`

Example 2:

If the passed parameter is a positive number but fractional.

```
<script type="text/javascript"> 
   document.write(Math.fround(3.345));           
</script> 
```

Output:

`3.3450000286102295`

Example 3:

If the passed parameter is a negative number

```
<script type="text/javascript"> 
   document.write(Math.fround(-3));           
</script> 
```

Output:

`-3`

Example 4:

If the passed parameter is a negative number but fractional

```
<script type="text/javascript"> 
   document.write(Math.fround(-3.345));           
</script> 
```

Output:

`-3.3450000286102295`

Example 5:

If the passed parameter is 0

```
<script type="text/javascript"> 
   document.write(Math.fround(0));           
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