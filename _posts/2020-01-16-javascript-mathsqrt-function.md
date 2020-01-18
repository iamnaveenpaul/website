---
title: JavaScript Math.sqrt() function
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

The JavaScript Math.sqrt() method is used to find square root of the number provided to the function as a parameter.

**Syntax**

`Math.sqrt(value)`

**Parameters:**

This method takes a single parameter value that contains the number that determines the square root of.

**Returns:**

Square root of the given number as value is passed as a parameter.

Example:

```
Input  : Math.sqrt(4)
Output : 2
```

```
Input  : Math.sqrt(-4)
Output : NaN
```

**Errors and Exceptions:**

NaN is returned if:

* A non-numeric string passed as the parameter.
* An array that has passed more than 1 integer as parameter.
* A passed negative number as parameter.
* A passed empty string as parameter.
* A passed empty array as parameter.

Example 1:

```
<!-- NEGATIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.sqrt(-2) + "<br>");  
    document.write(Math.sqrt(-2.56));           
</script> 
```

Output:

```
NaN
NaN
```

Example 2:

```
<!-- POSITIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.sqrt(2) + "<br>");  
    document.write(Math.sqrt(2.56));           
</script> 
```

Output:

```
1.4142135623730951
1.6
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

`4.06201920231798`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari