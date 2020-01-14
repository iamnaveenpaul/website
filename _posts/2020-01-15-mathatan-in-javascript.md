---
image: "/assets/default-social-image.png"
title: Math.atan() In JavaScript
categories: JavaScript-math
---

For JavaScript, the Math.atan() method is used to obtain the arctangent of a number in radians.

```
Math.atan(x)=arctan(x)=unique y,where y belongs to [-pi/2;pi/2] 
such that tan(y)=x
```

The method Math.atan() produces a numerical value between the radians -pi/2 and pi/2.

atan() is a static method of Math, and is therefore always used as Math.atan(), rather than as a means of constructing a Math object.

**Syntax:**

`Math.atan(value)`

**Parameters:**

This method takes a single parameter that is a number in the radians you want to find arctangent to.

**Returns:**

In radians, the function Math.atan() returns the arctangent of the given number.

Examples:

```
Input  : Math.atan(1)
Output : 0.7853981633974483
```
     
```
Input  : Math.atan(0)
Output : 0
```

```
Input  : Math.atan(-0)
Output : -0
```

```
Input  : Math.atan(Infinity)
Output : 1.5707963267948966
```

```
Input  : Math.atan(-Infinity)
Output : -1.5707963267948966
```

Example 1:

When a parameter passed is 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atan(1)); 
</script> 
```

Output:

`Output : 0.7853981633974483`

Example 1:

When a parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atan(0)); 
</script> 
```

Output:

`Output : 0`

Example 1:

When a parameter passed is 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atan(-0)); 
</script> 
```

Output:

`Output : -0`

Example 1:

When a parameter passed is Infinity.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atan(Infinity)); 
</script> 
```

Output:

`Output : 1.5707963267948966`

Example 1:

When a parameter passed is Infinity.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.atan(-Infinity)); 
</script> 
```

Output:

`Output : -1.5707963267948966`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari