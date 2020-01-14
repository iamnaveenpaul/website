---
image: "/assets/default-social-image.png"
title: Math.asinh() In JavaScript
categories: JavaScript-math
---

The function Math.asinh() returns the hyperbolic arc-sine of a number. The asinh() is Math's static method, so it is always used as Math.asinh(), rather than as a procedure of creating a math object.

**Syntax:**

`Math.asinh(value)`

**Parameter:**

This function accept single parameter value which is the number whose hyperbolic arc-sine you want to know.

**Returns:**

It returns the given number to the hyperbolic arc-sine.

Examples:

```
Input  : Math.asinh(2)
Output : 1.4436354751788103
```

```
Input  : Math.asinh(0)
Output : 0
```

```
Input  : Math.asinh(-1)
Output : -0.881373587019543
```

Example 1:

```
<script type = "text/javascript"> 
 
   // 2 is passed as a parameter 
   document.write("Output : " + Math.asinh(2)); 
</script> 
```

Output:

`Output : 1.4436354751788103`

Example 2:

```
<script type = "text/javascript"> 
 
   // 0 is passed as a parameter 
   document.write("Output : " + Math.asinh(0)); 
</script> 
```

Output:

`Output : 0`

Example 3:

```
<script type = "text/javascript"> 
 
   // 1 is passed as a parameter 
   document.write("Output : " + Math.asinh(1)); 
</script> 
```

Output:

`Output : 0.881373587019543`

Example 4:

```
<script type = "text/javascript"> 
 
   // -1 is passed as a parameter 
   document.write("Output : " + Math.asinh(-1)); 
</script> 
```

Output:

`Output : -0.881373587019543`

**Supported Browsers:**

* Google Chrome 38.0
* Internet Explorer 12.0
* Firefox 25.0
* Opera 25.0
* Safari 8.0