---
title: JavaScript Math.round() function
image: "/assets/default-social-image.png"
categories: JavaScript-math
---

For JavaScript, the Math.round() method is used to round the number passed to its closest integer as a parameter.

**Syntax**

`Math.round(value)`

**Parameters:**

The rounded number to its closest integer value.

**Returns :**

Result after the amount passed as parameter to the function passed as parameter has been rounded.

The math.round() method should be applied in the following way to round out a number to its nearest integer:

```
<script type="text/javascript"> 
    var round =Math.round(5.8); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

`Number after rounding : 6`

To round out a negative number to its nearest integer, the method Math.round() should be implemented as follows:

```
<script type="text/javascript"> 
    var round =Math.round(-5.8); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

`Number after rounding : -6`

If the parameter has ".5" as decimal, the function Math.round() indicates the value of the function Math.round() as shown below:

```
<script type="text/javascript"> 
    var round =Math.round(-12.5); 
    document.write("Number after rounding : " + round); 
    var round =Math.round(12.51); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

```
Number after rounding : -12
Number after rounding : 13
```

**Errors and Exceptions**

The following will result as NaN output:

1. If a non-numeric string passed as parameter
2. An array that has passed more than 1 integer as parameter.
3. If an empty variable is passed as parameter.
4. An empty string passed as parameter.
5. An empty array passed as parameter.

Example:

```
<!-- NEGATIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.round(-2));  
    document.write(Math.round(-2.56));           
</script> 
```

Output:

```
-2
-3
```

```
<!-- POSITIVE NUMBER EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.round(2));  
    document.write(Math.round(2.56));           
</script> 
```

Output:

```
2
3
```

```
<!-- STRING EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.floor("GrivaForCoding"));           
</script> 
```

Output:

`NaN`

```
<!-- ADDITION INSIDE FUNCTION EXAMPLE -->
<script type="text/javascript"> 
    document.write(Math.floor(7.2+9.3));            
</script> 
```

Output:

`17`