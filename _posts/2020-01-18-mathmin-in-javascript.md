---
image: "/assets/default-social-image.png"
title: Math.min() In JavaScript
categories: JavaScript-math
---

The function Math.min() is used to return the number passed in the method with the lowest-value. The method Math.min() returns NaN when parameter is not a number and can not be transformed into one. The min() is Math's static method so it is always used as Math.min() rather than as a tool of constructing a Math object.

**Syntax:**

`Math.min(value1, value2, ...)`

**Parameters:**

This method takes Value1,Value2 values passed to the function math.min() in order to calculate the lowest valued number.

**Return Value:**

The method Math.min() returns the lesser value of the specified numbers.

Examples:

```
Input  : Math.min(10, 32, 2)
Output : 2
```
     
```
Input  : Math.min(-10, -32, -1)
Output : -32
```

```
Input  : Math.min()
Output : -Infinity
```

```
Input  : Math.min(10,2,NaN)
Output : NaN
```

Example 1:

If passing the parameter as a positive number.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.min(10, 32, 2)); 
</script> 
```

Output:

`Output : 2`

Example 2:

If passing the parameter as a negative number.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.min(-10, -32, -1)); 
</script> 
```

Output:

`Output : -32`

Example 3:

If passing no parameters.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.min()); 
</script> 
```

Output:

`Output : -Infinity`

Example 4:

If passing the parameter as NaN.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.min(10,2,NaN)); 
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