---
image: "/assets/default-social-image.png"
title: Math.tan() In JavaScript
categories: JavaScript-math
---

In Javascript, the Math.tan() method is used to calculate a number's tangent value.

The method Math.tan() returns a number which represents the angle value of tangent.

tan() is a static method in Math, so it's only used as Math.tan() rather than as a means of constructing a Math object.

**Syntax:**

`Math.tan(value)`

**Parameters:**

This method accepts a single value parameter, a number indicating an angle in radians.

**Returns:**

The method Math.tan() returns the tangent value of the given number.

Examples:

```
Input  : Math.tan(0)
Output : 0
```
     
```
Input  : Math.tan(1)
Output : 1.557407724654902
```

```
Input  : Math.tan(Math.PI / 4)
Output : 0.9999999999999999
```

Example:

If the parameter is passed as 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.tan(0)); 
</script> 
```

Output:

`Output : 0`

Example 2:

If the parameter is passed as 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.tan(1)); 
</script> 
```

Output:

`Output : 1.557407724654902`

Example 3:

If the parameter is passed as PI.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.tan(Math.PI / 4)); 
</script> 
```

Output:

`Output : 0.9999999999999999`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari