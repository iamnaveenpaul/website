---
image: "/assets/default-social-image.png"
title: JavaScript Math.tanh() function
categories: JavaScript-math
---

The Math.tanh() is a JavaScript built-in function that is used to measure a number's hyperbolic tangent value.

**Syntax:**

`Math.tanh(p)`

**Parameter:**

This method takes a single parameter p which is a number that will determine the hyperbolic tangent value for.

**Return value:**

This returns the numeral hyperbolic tangent measured value.

Examples:

```
Input :Math.tanh(0)
Output:0
```

**Explanation:**

The formula for calculating any number's hyperbolic tangent is: The number e is a mathematical constant with an approximate value of 2.718.

`tanh(p) = sinh(p)/cosh(p) = e^p-e^-p/e^p+e^-p = e^0-e^-0/e^0+e^-0 = 0 `

Hyperbolic tangent of any number can be determined in the same way just after replacing p with the appropriate number.

```
Input :Math.tanh(18)
Output:0.9999999999999996
```

**Explanation:**

In this case, the same as above equation, if we placed 18 instead of p then the value is as shown above.

Example 1:

```
<script> 
  // Printing hyperbolic tangent of some numbers 
  // taken as parameter of Math.tanh() function. 
  document.write(Math.tanh(0)); 
  document.write(Math.tanh(1)); 
  document.write(Math.tanh(5)); 
  document.write(Math.tanh(22)); 
  document.write(Math.tanh(-2)); 
  document.write(Math.tanh(4)); 
</script> 
```

Output:

```
0
0.7615941559557649
0.9999092042625951
1
-0.9640275800758169
0.999329299739067
```

Example 2:

It is an error scenario since it is impossible to take complex number as the function parameter and just an integer value can be used as parameter.

```
<script> 
  // complex number can not be calculated as the hyperbolic tangent. 
  documnet.write(Math.tanh(1 + 2i)); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

Apart from integer, nothing is agreed as the function parameter which is why the string here as the parameter gives NaN i.e. not a number.

```
<script> 
  // Any string value as the parameter of the function 
  // gives NaN i.e, not a number 
  // because only number can be used as the parameters. 
  document.write(Math.tanh("geeksforgeeks")); 
  document.write(Math.tanh("gfg")); 
</script> 
```

Output:

```
NaN
NaN
```

**Application:**

The practical application is that we take the advantage of Math.tanh() method in JavaScript when we need to calculate the hyperbolic tangent value of a number each time.

Example:

```
<script> 
  // Printing hyperbolic tangent of some  
  //numbers from 0 to 9 
  // taken as parameter of Math.tanh() function. 
  for (i = 0; i < 10; i++) 
  { 
     document.write(Math.tanh(i) + "<br>"); 
  } 
</script>
```

Output:

```
0
0.7615941559557649
0.9640275800758169
0.9950547536867305
0.999329299739067
0.9999092042625951
0.9999877116507956
0.9999983369439447
0.9999997749296758
0.999999969540041
```

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari