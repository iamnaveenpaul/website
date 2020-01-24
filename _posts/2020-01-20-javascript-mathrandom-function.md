---
image: "/assets/default-social-image.png"
title: JavaScript Math.random() function
categories: JavaScript-math
---

The function Math.random() is used to revert back a pseudo-random number floating-point between range  (0,1), 0 (inclusive) and 1 (exclusive) range. This random number could then be adjusted to the ideal range.

Syntax:

`Math.random();`

**Parameters:**

This function requires no parameters.

**Return Value:**

The method math.random() returns a pseudo-random number in range (0,1), 0 (inclusive) and 1 (exclusive) floating point.

Example 1:

To get a random number from 0(inclusive) to 1(exclusive), you can implement the following code:

```
<script type="text/javascript"> 
    var random = Math.random( ); 
    document.write("Random Number Generated : " + random );  
</script> 
```
     
Output:

`Random Number Generated : 0.2894437916976895`

Example 2:

Math.random() could be used to get a random number between two numbers. The return value is no less than min, and may be equivalent to min, and may be less than and not equal to max.

The method math.random() can be executed in the following manner to get a random number between two values:

```
<script type="text/javascript"> 
    var min=4; 
    var max=5;  
    var random = Math.random() * (+max - +min) + +min; 
    document.write("Random Number Generated : " + random );  
</script> 
```

Output:

`Random Number Generated : 4.991720937372939`

Example 3:

Math.random() is used to get an integer between two numbers. The return value is no less than min, or if min is not an integer, it is the next integer greater than min. It is also less than but not equal to max.

The Math.random() method can be performed in the following manner to get a random integer between two values:

```
<script type="text/javascript"> 
    var min=4; 
    var max=5;  
    var random = 
    Math.floor(Math.random() * (+max - +min)) + +min; 
    document.write("Random Number Generated : " + random );  
</script> 
```

Output:

`Random Number Generated : 4`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari