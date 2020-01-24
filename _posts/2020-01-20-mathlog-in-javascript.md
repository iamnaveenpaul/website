---
image: "/assets/default-social-image.png"
title: Math.log() In JavaScript
categories: JavaScript-math
---

In JavaScript, the Math.log() method is used to calculate a number's natural logarithm (base e). In mathematics, the function of JavaScript Math.log() is analogous to ln(x).

If x's value is negative, then the function math.log() returns NaN.

Log() is a static Math method thus it is used as Math.log() instead of as a method of the constructed Math object.

Syntax:

`Math.log(value)`

**Parameters:** 

This method recognizes a single parameter value which is the number that you want to find in the natural logarithm.

**Returns:**

The function Math.log() returns the given number to the natural logarithm.

Examples:

When the parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.log(0)); 
</script> 
```

Output:

`Output : -Infinity`

When the parameter passed is -1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.log(-1)); 
</script> 
```

Output:

`Output : NaN`

When the parameter passed is 10.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.log(10)); 
</script> 
```

Output:

`Output : 2.302585092994046`

**Calculating Math.log() with a different base.**

To find a logarithm of 8 with base 2, implement the function math.log() as follows:

```
<script type="text/javascript"> 
   document.write("Output : " + Math.log(8)/Math.log(2)); 
</script> 
```

Output:

`Output : 3`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari