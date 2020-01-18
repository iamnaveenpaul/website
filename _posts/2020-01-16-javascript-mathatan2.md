---
image: "/assets/default-social-image.png"
title: JavaScript Math.atan2()
categories: JavaScript-math
---

For JavaScript, the Math.atan2() method is used to calculate the quotient arctangent of its arguments. The method Math.atan2() produces a numerical value between  -Π and Π describing the angle theta of a point (x, y) and the positivex-axis. This is the counterclockwise angle between the positive X-axis and the position (x, y), calculated in radians.

**Syntax:**

`Math.atan2(value1, value2)`

**Parameters:**

This method recognizes the value1 and value2 for two parameters. The value1 represents the y-coordintae and the value2 represents the point(x, y) of x-coordinate.

**Returns:**

This returns the arguments to the arctangent of the quotient.

Examples:

```
Input  : Math.atan2(90, 15);  
Output : 1.4056476493802699
```

```
Input  : Math.atan2(15, 90);
Output : 0.16514867741462683
```

Example 1:

Where y-coordinate exceeds x-coordinate:

```
<script type="text/javascript"> 
   document.write(Math.atan2(90, 15));   
</script> 
```

Output:

`1.4056476493802699`

Example 2:

When y is smaller than x-coordinate

```
<script type="text/javascript"> 
   document.write(Math.atan2(15, 90));   
</script> 
```

Output:

`0.16514867741462683`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari