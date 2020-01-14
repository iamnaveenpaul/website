---
image: "/assets/default-social-image.png"
title: JavaScript Math.cbrt() function
categories: JavaScript-math
---

The function Math.cbrt() is a built-in JavaScript function that is used for finding a number's cube root value.

**Syntax:**

`Math.cbrt(x)`

**Parameters:**

This method recognizes a single parameter, which is simply a number that needs to be found by cube root.

**Returns:**

The cube root of the given number is returned.

Example:

```
Input  : Math.cbrt(8)
Output : 2
```

**Explanation:**

```
∛8
= ∛2*2*2
= 2
```

Here the cube root of 8 is determined to 2 because for the cube root, just one number is taken out as the value of the cube root when any 3 times repeated number is present.

Example 1:

Cube root of multiple numbers:

```
<script type="text/javascript">  
   document.write("Output : " + Math.cbrt(64) + "<br>"); 
   document.write("Output : " + Math.cbrt(27) + "<br>");  
   document.write("Output : " + Math.cbrt(0) + "<br>");  
   document.write("Output : " + Math.cbrt(-1) + "<br>");  
   document.write("Output : " + Math.cbrt(-27) + "<br>");  
   document.write("Output : " + Math.cbrt(Infinity));  
</script>  
```

Output:

```
Output : 4
Output : 3
Output : 0
Output : -1
Output : -3
Output : Infinity
```

Example 2:

Errors and Exceptions: this is an error case because it is not possible to find the cube root of the complex number which is why its parameter yields error.

```
<script type="text/javascript">  
  // cube root of complex number can not be calculated. 
  document.write("Output : " + Math.cbrt(1 + 2i)); 
</script>  
```

Output:

`Error: Invalid or unexpected token`

Example 3:

It is not possible to find the cube root of string which is why the function's string parameter yields NaN, i.e. not a number. Only integer value can be used as function parameter.

```
<script type="text/javascript">  
   // Only number can be used as the parameter 
   // here string as parameter gives NaN i.e, not a number. 
   document.write("Output : " + Math.cbrt("gfg")); 
</script>  
```

Output:

`Output: NaN`

**Application:**

Whenever we need to get the cube root of any number that moment in JavaScript, we seek the help of the function Math.cbrt().

Example:

```
<script type="text/javascript">  
// Here the Math.cbrt() function calculates cube root for 
// different numbers taken as function's parameter. 
   document.write("Output : " + Math.cbrt(125) + "<br>"); 
   document.write("Output : " + Math.cbrt(23) + "<br>");  
</script>  
```

Output:

```
Output : 5
Output : 2.8438669798515654
```

**Supported Browsers:**

* Google Chrome 38.0
* Internet Explorer 12.0
* Firefox 25.0
* Opera 25.0
* Safari 8.0