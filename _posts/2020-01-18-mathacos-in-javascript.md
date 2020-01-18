---
image: "/assets/default-social-image.png"
title: Math.acos() In JavaScript
categories: JavaScript-math
---

For JavaScript, the Math.acos() function is used to calculate the arccosine of a number in radians.

```
Math.acos(x)=arccos(x)=unique y,
where y belongs to [0;pi] 
such that cos(y)=x
```

The method Math.acos() returns a numerical value between radians 0 and pi.

acos() is a static method of Math, and is thus always used as Math.acos(), rather than as a method of constructing a Math object.

**Syntax:**

`Math.acos(value)`

**Parameters:**

This function recognizes single parameter value that is a number in radians we want to find of arccosine value.

**Returns:**

In radians, the function Math.acos() returns the arccosine of the given number.

Examples:

```
Input  : Math.acos(1)
Output : 0
```
     
```
Input  : Math.acos(-1)
Output : 3.141592653589793
```

```
Input  : Math.acos(0)
Output : 1.5707963267948966
```

```
Input  : Math.acos(0.5)
Output : 1.0471975511965979
```

```
Input  : Math.acos(2)
Output : NaN
```

Example 1: 

When the parameter is passed as 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acos(1)); 
</script> 
```

Output:

`Output : 0`

Example 2:

When the parameter is passed as -1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acos(-1)); 
</script> 
```

Output:

`Output : 3.141592653589793`

Example 3:

When the parameter is passed as 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acos(0)); 
</script> 
```

Output:

`Output : 1.5707963267948966`

Example 4:

When the parameter is passed as 0.5.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acos(0.5)); 
</script> 
```

Output:

`Output : 1.0471975511965979`

Example 5:

When the parameter is passed as 2.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.acos(2)); 
</script> 
```

Output:

`Output : NaN`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari