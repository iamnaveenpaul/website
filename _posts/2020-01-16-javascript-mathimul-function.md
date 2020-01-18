---
image: "/assets/default-social-image.png"
title: JavaScript Math.imul() Function
categories: JavaScript-math
---

In JavaScript, the Math.imul() function is used to calculate the result of the 32-bit multiplication of the two integers passed as parameters. Math.imul() allows multiplication of 32-bit integer with C-like semantics. If the method Math.imul() is used in JavaScript for regular floating type variables then a reduction in efficiency would arise due to the translation of floats to ints before multiplication. If the Math.imul() method is used with standard floating-point variables enabled in JavaScript, the overhead of conversion results in a performance degrade.

**Syntax:**

`Math.imul(Value1, Value2);`

**Parameters:**

This function accepts two parameters Value1 and Value2 which describes two multipliable numbers.

**Return Value:**

The method Math.imul() returns the product of equivalent to C 32-bit multiplication of the provided arguments.

Examples:

```
Input  : Math.imul(3, 4)
Output : 12
```
     
```
Input  : Math.imul(-3, -4)
Output : 12
```

```
Input  : Math.imul(0, 4)
Output : 0
```

Example 1:

When it passes two positive numbers as parameters.

```
<script type="text/javascript"> 
   document.write(Math.imul(3, 4)); 
</script> 
```

Output:

`12`

Example 2:

When both numbers are passed as parameters (of the opposite sign)

```
<script type="text/javascript"> 
   document.write(Math.imul(0xfffffffe, 4)); 
</script> 
```

Output:

`-8`

Example 3:

When passing Two negative numbers as parameters.

```
<script type="text/javascript"> 
   document.write(Math.imul(-3, -4)); 
</script> 
```

Output:

`12`

Example 4:

While passing one of the parameters as zero.

```
<script type="text/javascript"> 
   document.write(Math.imul(0, 4)); 
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