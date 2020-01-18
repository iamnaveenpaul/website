---
image: "/assets/default-social-image.png"
title: Math.cos() In JavaScript
categories: JavaScript-math
---

For Javascript, the Math.cos() method is used to calculate a number's cosine value.

The method Math.cos() returns a numerical value between -1 and 1 which represents the angle cosine provided in the radians. The cos() is Math's static method so it is always used as Math.cos() rather than as a method of a constructed Math object.

**Syntax:**

`Math.cos(value)`

**Parameters:**

This function recognizes a single parameter that is a specified number value in radians.

**Returns:**

The function Math.cos() returns the cosine of the specified number which ranges between -1 and 1.

Examples:

If the parameter is passed as 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.cos(0)); 
</script> 
```

Output:

`Output : 1`

If the parameter is passed as 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.cos(1)); 
</script> 
```

Output:

`Output : 0.5403023058681398`

If the parameter is passed as PI.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.cos(Math.PI)); 
</script> 
```

Output:

`Output : -1`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari