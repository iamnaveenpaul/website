---
image: "/assets/default-social-image.png"
title: Math.exp() In JavaScript
categories: JavaScript-math
---

In JavaScript, the Math.exp() method is used to return ex, where x is the argument, and e is the Euler number, the base of the natural logarithms.

exp() is a static method of Math, therefore it is always used as Math.exp() instead of as a function of the generated Math object.

**Syntax:**

`Math.exp(value)`

**Parameters Used:**

This function recognizes a single parameter value, which is the number you want to find the ex.

**Returns:**

The function Math.exp() returns ex where e is the Euler number and x is the argument.

Examples:

When a parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.exp(0)); 
</script> 
```

Output:

`Output : 1`

When a parameter passed is -1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.exp(-1)); 
</script> 
```

Output:

`Output : 0.36787944117144233 `

When a parameter passed is 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.exp(1)); 
</script> 
```

Output:

`Output :  2.718281828459045 `

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari