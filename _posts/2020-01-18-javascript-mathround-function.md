---
image: "/assets/default-social-image.png"
title: JavaScript Math.round() function
categories: JavaScript-math
---

In JavaScript, the Math.round() method is used to round a quantity to its closest integer value. The argument is rounded to the next higher integer if the fractional element of the amount is greater than or equal to .5, and is rounded to the next lower integer if the amount is less than .5.

**Syntax:**

`Math.round(var);`

**Parameters:**

This method requires only parameter, var. It is the number you'd like to round it off.

**Return Value:**

The method Math.round() returns the value of the specified rounded number to the nearest integer.

Example 1:

The math.round() method should be implemented in the following manner for rounding out a number towards its closest integer value:

```
<script type="text/javascript"> 
    var round =Math.round(5.8); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

`Number after rounding : 6`

Example 2:

The method Math.round() rounds off a negative number if passed to it as a parameter. The Math.round() method should be implemented in the following manner to round out a negative value towards its closest integer:

```
<script type="text/javascript"> 
    var round =Math.round(-5.8); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

`Number after rounding : -6`

Example 3:

The example below demonstrates the output of the Math.round() method when the decimal parameter is set to ".5."

```
<script type="text/javascript"> 
    var round =Math.round(-12.5); 
    document.write("Number after rounding : " + round + 
    "<br>"); 
    var round =Math.round(12.51); 
    document.write("Number after rounding : " + round);  
</script> 
```

Output:

```
Number after rounding : -12
Number after rounding : 13
```

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari