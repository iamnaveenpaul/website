---
image: "/assets/default-social-image.png"
title: JavaScript Math.atanh()
categories: JavaScript-math
---

For JavaScript, the Math.atanh() method is used to return a number's hyperbolic arctangent.

`Math.atanh (x) = arctanh(x) = y such that tanh (y) = x`

atanh() is a static Math method so it is always used as Math.atanh() instead as a means of constructing a Math object.

**Syntax:**

`Math.atanh(value)`

**Parameters:**

This method recognizes a single value parameter which is the number that you want to know about the hyperbolic arc-tangent.

**Returns:**

It returns the specified number's hyperbolic Arc-tangent.

Examples:

```
Input  : Math.atanh(1)
Output : Infinity
```

```
Input  : Math.atanh(0)
Output : 0
```

```
Input  : Math.atanh(2)
Output : NaN
```

```
Input  : Math.atanh(0.5)
Output : 0.5493061443340548
```

Example 1:

When a parameter passed is 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atanh(1)); 
</script> 
```

Output:

`Output : Infinity`

Example 2:

When a parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atanh(0)); 
</script> 
```

Output:

`Output : 0`

Example 3:

When a parameter passed is 2.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atanh(2)); 
</script> 
```

Output:

`Output : NaN`

Example 4:

When a parameter passed is 0.5.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atanh(0.5)); 
</script> 
```

Output:

`Output : 0.5493061443340548`

**Supported Browsers:**

* Google Chrome 38.0
* Internet Explorer 12.0
* Firefox 25.0
* Opera 25.0
* Safari 8.0