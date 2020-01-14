---
title: Math.acosh() In JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

In Javascript the Math.acosh() function is used to return a number's hyperbolic arc-cosine.

`Math.acosh (x) = arcosh(x) = y ≧ 0 such that cosh (y)=x`

acosh() is a static method of Math, and is thus always used as Math.acosh() rather than as a means of constructing a Math object.

**Syntax:**

`Math.acosh(value)`

**Parameters:**

This function accepts a single parameter value which is the number which you want to know about the hyperbolic arc-cosine.

**Returns:**

It returns the hyperbolic arc-cosine of the number given and if the passed parameter is less than 1, it returns NaN.

Examples:

```
Input  : Math.acosh(1)
Output : 0
```

```
Input  : Math.acosh(0)
Output : NaN
```

```
Input  : Math.acosh(-1)
Output : NaN
```

```
Input  : Math.acosh(2)
Output : 1.3169578969248166
```

Example 1:

When the parameter passed is 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acosh(1)); 
</script> 
```

Output:

`Output : 0`

Example 2:

When the parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acosh(0)); 
</script> 
```

Output:

`Output : NaN`

Example 3: 

When the parameter passed is less than 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acosh(-1)); 
</script> 
```

Output:

`Output : NaN`

Example 4:

When the parameter passed is 2.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acosh(2)); 
</script> 
```

Output:

`Output : 1.3169578969248166`

**Supported Browsers:**

* Google Chrome 38.0
* Internet Explorer 12.0
* Firefox 25.0
* Opera 25.0
* Safari 8.0