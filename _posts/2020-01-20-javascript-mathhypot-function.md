---
title: JavaScript Math.hypot() Function
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

In JavaScript, the Math.hypot() function is used to calculate the square root of the sum of squares of numbers carried as arguments.

Generally, it is used to calculate a right-angled triangle hypotenuse, or the magnitude of a complex number. Math.hypot() uses the `Math.sqrt(v1*v1 + v2*v2)` function where v1 and v2 are either the sides of the triangle, or the real and complex numbers.

The hypot() is Math's static method and is thus used as Math.hypot() and not as a tool of constructing a Math object.

Syntax:

`Math.hypot(value1, value2,....)`

**Parameters:**

The function Math.hypot() accepts a list of numbers as parameters separated by the operator comma (,). In the above syntax, value1, value2 are values that the user wants to send to the function hypot().

**Return Value:**

The function Math.hypot() returns the square root of the passed arguments sum of squares. It returns NaN when you can not convert at least one of the arguments to a number.

Example 1:

If it passes two positive numbers as parameters:

```
<script type="text/javascript"> 
   document.write(Math.hypot(3, 4));           
</script> 
```

Output:

`5`

Example 2:

If it passes two negative numbers as parameters:

```
<script type="text/javascript"> 
   document.write(Math.hypot(-3, -4));           
</script> 
```

Output:

`5`

Example 3:

If it passes more than two positive numbers as parameters:

```
<script type="text/javascript"> 
   document.write(Math.hypot(3, 6, 7));  
</script> 
```

Output:

`9.695359714832659`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari