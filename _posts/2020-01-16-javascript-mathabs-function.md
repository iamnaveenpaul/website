---
title: JavaScript Math.abs() function
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

In JavaScript, the Math.abs() method is used to calculate the absolute value of a number. As parameter, it takes a number and returns its absolute value.

**Syntax:**

`Math.abs(value)`

**Parameters:**

The number for absolute value of which is to be found passes to this function as the parameter.

**Returns:**

Absolute value of passed number as parameter.

**Example:**

```
Input  : Math.abs(-4)
Output : 4
```

```
Input  : Math.abs(0)
Output : 0
```

**Errors and Exceptions:**

1. NaN is returned for a non-numeric string passed as parameter.
2. NaN is returned for an array that has passed more than 1 integer as parameter.
3. NaN is returned for an empty variable passed as parameter
4. A passed empty string as parameter returns 0
5. A passed empty array as parameter returns 0

Example 1:

```
<!-- NEGATIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.abs(-2));  
    document.write(Math.abs(-2.56));           
</script> 
```

Output:

```
2
2.56
```

Example 2:

```
<!-- POSITIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.abs(2));  
    document.write(Math.abs(2.56));           
</script> 
```

Output:

```
2
2.56
```

Example 3:

```
<!-- STRING EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.abs("GrivaForCoding"));           
</script> 
```

Output:

`NaN`

Example 4:

```
<!-- ADDITION INSIDE FUNCTION EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.abs(7+9));            
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