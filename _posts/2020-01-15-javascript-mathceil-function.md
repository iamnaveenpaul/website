---
title: JavaScript Math.ceil() function
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

For JavaScript, the Math.ceil() method is used to round the number passed as a parameter to its closest integer for rounding direction upwards, i.e. towards the higher value.

**Syntax**

`Math.ceil(value)`

**Parameters:**

This function takes a single parameter which is the amount to be rounded in upward rounding process to its nearest integer.

**Returns:**

The output after the number passed to the function as parameter is rounded.

Examples:

```
Input  : Math.ceil(4.23)
Output : 5
```

```
Input  : Math.ceil(0.8)
Output : 1
```

**Errors and Exceptions:**

The following yeilds NaN as output:

1. A parameter passed non-numeric array.
2. An array that has passed more than 1 integer as parameter.
3. A parameter passed empty variable.
4. A parameter passed empty string.
5. A parameter passed empty array.

Example: 1

```
<!-- NEGATIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.ceil(-2) + "<br>");  
    document.write(Math.ceil(-2.56));           
</script> 
```

Output:

```
-2
-2
```

Example:2

```
<!-- POSITIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.ceil(2) + "<br>");  
    document.write(Math.ceil(2.56));           
</script> 
```

Output:

```
2
3
```

Example 2:

```
<!-- STRING EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.ceil("GrivaForCoding"));           
</script> 
```

Output:

`NaN`

Example:3

```
<!-- ADDITION INSIDE FUNCTION EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.ceil(7+9));            
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