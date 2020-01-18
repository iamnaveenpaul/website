---
image: "/assets/default-social-image.png"
title: Math.max() In JavaScript
categories: JavaScript-math
---

The method Math.max() is used to calculate the largest of zero or more number value.

If no arguments are passed, the result is "-Infinity" and the result is NaN if at least one of the arguments could not be transformed to a number.

max() is a static method of Math, so it is always used as Math.max() rather than as a method of the created Math object.

**Syntax:**

`Math.max(value1, value2, ...)`

**Parameters:**

This fucntion takes Value1, Value2 sent to the function math.max() to find the highest value.

**Returns:**

The function Math.max() returns the greatest value of the specified numbers.

Examples:

```
Input  : Math.max(10, 32, 2)
Output : 32
```
     
```
Input  : Math.max(-10, -32, -1)
Output : -1
```

```
Input  : Math.max()
Output : -Infinity
```

```
Input  : Math.max(10,2,NaN)
Output : Nan
```

Example 1:

If passing parameters as positive numbers.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.max(10, 32, 2)); 
</script> 
```

Output:

`Output : 32`

Example 2:

If passing parameters as negative numbers.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.max(-10, -32, -1)); 
</script> 
```

Output:

`Output : -1`

Example 3:

If passing no parameters.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.max()); 
</script> 
```

Output:

`Output : -Infinity`

Example 4:

If passing parameters as NaN.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.max(10,2,NaN)); 
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