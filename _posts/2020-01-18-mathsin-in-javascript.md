---
image: "/assets/default-social-image.png"
title: Math.sin() In JavaScript
categories: JavaScript-math
---

In Javascript, the Math.sin() method is used to calculate a number's sine value.

The method Math.sin() returns a numerical value between -1 and 1 that represents the angle of sine provided in the radians.

sin() is a static form of Math, and is thus only used as Math.sin() rather than as a method of constructing a Math object.

**Syntax:**

`Math.sin(value)`

**Parameters:**

This function recognizes the value of a single parameter that is a number value provided in radians.

**Return Value:**

The method Math.sin() returns the sine value for the specified numbers.

Examples:

```
Input  : Math.sin(0)
Output : 0
```
     
```
Input  : Math.sin(1)
Output : 0.8414709848078965
```

```
Input  : Math.sin(Math.PI / 2)
Output : 1
```

Example:

If the parameter is passed as 0.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.sin(0)); 
</script> 
```

Output:

`Output : 0`

Example 2:

If the parameter is passed as 1.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.sin(1)); 
</script> 
```

Output:

`Output : 0.8414709848078965`

Example 3:

If the parameter is passed as PI.

```
<script type="text/javascript"> 
   document.write("Output : " + Math.sin(Math.PI / 2)); 
</script> 
```

Output:

`Output : 1`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari