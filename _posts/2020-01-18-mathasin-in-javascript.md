---
image: "/assets/default-social-image.png"
title: Math.asin() In JavaScript
categories: JavaScript-math
---

The Math.asin() method is used to calculate the arcsine of a number in radians.

```
Math.asin(x)=arcsin(x)=unique y,where y belongs to [-pi/2;pi/2]
such that sin(y)=x
```

The function Math.asin() produces a numerical value between the radians -pi/2 and pi/2.

asin() is a static method of Math, and is therefore always used as Math.asin(), rather than as a tool of creating a Math object.

**Syntax:**

`Math.asin(value)`

**Parameters:**

This method takes a single parameter that is the number of radians whose value we want to find in the arcsine.

**Returns:**

The function Math.asin() returns the arcsine in radians with the given number.

Examples:

```
Input  : Math.asin(1)
Output : 1.5707963267948966
```
     
```
Input  : Math.asin(-1)
Output : -1.5707963267948966
```

```
Input  : Math.asin(2)
Output : NaN
```

```
Input  : Math.asin(0.5)
Output : 0.5235987755982989
```

Example 1:

When the parameter is passed as 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.asin(1)); 
</script> 
```

Output:

`Output : 1.5707963267948966`

Example 2:

When the parameter is passed as -1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.asin(-1)); 
</script> 
```

Output:

`Output : -1.5707963267948966`

Example 3:

When the parameter is passed as 2.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.asin(2)); 
</script> 
```

Output:

`Output : NaN`

Example 4:

When the parameter is passed as 0.5.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.asin(0.5)); 
</script> 
```

Output:

`Output : 0.5235987755982989`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari