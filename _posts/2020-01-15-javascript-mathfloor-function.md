---
image: "/assets/default-social-image.png"
title: JavaScript Math.floor() function
categories: JavaScript-math
---

For JavaScript, the Math.floor() method is used to round off the number passed as a parameter to its closest integer in the direction of rounding downwards, i.e. towards the smaller value.

**Syntax**

`Math.floor(value)`

**Parameters:**

This function takes a single parameter value in the downward rounding process that number to be rounded to its closest integer.

**Returns:**

Result after rounding the number passed to function passed as parameter.

Example:

```
Input  : Math.floor(4.23)
Output : 4
```

```
Input  : Math.floor(0.8)
Output : 0
```

**Errors and Exceptions:**

The following conditions yeilds NaN:

1. A parameter passed non-numeric string.
2. A parameter passed as array with more than 1 integer.
3. A parameter passed empty variable.
4. A parameter passed empty string.
5. A parameter passed empty array.

Example 1:

```
<script type="text/javascript"> 
    document.write(Math.floor(-2) + "<br>");  
    document.write(Math.floor(-2.56));           
</script> 
```

Output:

```
-2
-3
```

Example 2:

```
<!-- POSITIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.floor(2) + "<br>");  
    document.write(Math.floor(2.56));           
</script> 
```

Output:

```
2
2
```

Example 3:

```
<!-- STRING EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.floor("GrivaForCoding"));           
</script> 
```

Output:

`NaN`

Example 4:

```
<!-- ADDITION INSIDE FUNCTION EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.floor(7.2+9.3));            
</script> 
```

Output:

`16`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari