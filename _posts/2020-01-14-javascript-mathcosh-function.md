---
image: "/assets/default-social-image.png"
title: JavaScript Math.cosh() function
categories: JavaScript-math
---

Math.cosh() is a JavaScript built-in function that is used to measure the hyperbolic cosine value of a number.

**Syntax:**

`Math.cosh(p)`

**Parameter:**

This method acknowledges single parameter p, which is a number to determine the hyperbolic cosine value for.

**Returns:**

It returns the hyperbolic cosine calculated value of the number.

Examples:

```
Input  : Math.cosh(0)

Output : 1
```

**Explanation:**

Here, the formula for calculating any number's hyperbolic cosine, the number e is a mathematical constant with an approximate value 2.718.

```
 \frac{e^{p} + e^{-p}}{2} = \frac{e^{0} + e^{-0}}{2}   

 =\frac{1+1}{2}  
 = 1  
```

Likewise, you can measure hyperbolic cosine of any number just after replacing p with the desired value.

```
Input  :Math.cosh(12)

Output :81377.39571257407
```

Explanation:

In this case, just like the equation above, as we placed 12 instead of p, the value is as shown above.

Example 1:

```
<script> 
  // Printing hyperbolic cosine of some numbers 
  // taken as parameter of Math.cosh() function. 
  document.write(Math.cosh(0) + "<br>"); 
  document.write(Math.cosh(1) + "<br>"); 
  document.write(Math.cosh(0) + "<br>"); 
  document.write(Math.cosh(22) + "<br>"); 
  document.write(Math.cosh(-2) + "<br>"); 
  document.write(Math.cosh(4)); 
</script> 
```

Output:

```
 1
 1.5430806348152437
 1
 1792456423.065796
 3.7621956910836314
 27.308232836016487
```

Example 2:

Errors and Exceptions: this is an error case because it is not possible to take complex number as the function parameter, only integer value can be taken as parameter.

```
<script> 
  // complex number can not be calculated as the  
  //hyperbolic cosine. 
  document.write(Math.cosh(1 + 2i)); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

Apart from integer, nothing is acknowledged as the function parameter which is why the string here as the parameter gives NaN i.e. not a number.

```
<script> 
  // Any string value as the parameter of the function 
  // gives NaN i.e, not a number 
  // because only number can be used as the parameters. 
  document.write(Math.cosh("geeksforgeeks") + "<br>"); 
  document.write(Math.cosh("gfg"));                     
</script> 
```

Output:

```
NaN
NaN
```

**Application:**

Its practical application is that we use Math.cosh() function in JavaScript when we need to find the value of a number's hyperbolic cosine.

Example:

```
<script> 
  // Printing hyperbolic cosine of some numbers from 0 to 9 
  // taken as parameter of Math.cosh() function. 
  for (i = 0; i < 10; i++) { 
      document.write(Math.cosh(i) + "<br>"); 
  } 
</script> 
```

Output:

```
1
1.5430806348152437
3.7621956910836314
10.067661995777765
27.308232836016487
74.20994852478785
201.7156361224559
548.317035155212
1490.479161252178
4051.5420254925943
```

**Supported Browsers:**

* Google Chrome 38.0
* Internet Explorer 12.0
* Firefox 25.0
* Opera 25.0
* Safari 8.0