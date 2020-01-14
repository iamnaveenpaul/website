---
image: "/assets/default-social-image.png"
title: JavaScript Math.sinh() function
categories: JavaScript-math
---

Math.sinh() is a JavaScript built-in function which is used to calculate the hyperbolic sine value of a number.

**Syntax:**

`Math.sinh(p)`

**Parameter:**

This method acknowledges a single parameter p, a number that will be used to measure the hyperbolic sine value for.

**Returns:**

This returns the numeral hyperbolic sine measured value.

Examples:

```
Input  : Math.sinh(0)

Output : 0
```

**Explanation:**

Here formula for calculating any number's hyperbolic sine is: number e is a mathematical constant with an approximate value of 2,718.

```
  e^p-e^-^p/2  

 = e^0-e^-^0/2 
`
 = 1-1/2 

 = 0 
```

In the same way you can calculate hyperbolic sine of any number just after replacing p with the desired number.

```
Input  : Math.sinh(15)

Output : 1634508.6862359024
```

**Explanation:**

In this case, just like the calculation above, when we put 15 instead of p, the value becomes as shown above.

Example 1:

```
<script> 
  // Printing hyperbolic sine of some numbers 
  // taken as parameter of Math.sinh() function. 
  document.write(Math.sinh(0) + "<br>"); 
  document.write(Math.sinh(1) + "<br>"); 
  document.write(Math.sinh(5) + "<br>"); 
  document.write(Math.sinh(22) + "<br>"); 
  document.write(Math.sinh(-2) + "<br>"); 
  document.write(Math.sinh(4)); 
</script> 
```

Output:

```
0
1.1752011936438014
74.20321057778875
1792456423.065796
-3.626860407847019
27.28991719712775
```

Example 2:

It is an error case, because it is not possible to take complex number as the function parameter and only integer value could be held for it.

```
<script> 
  // complex number can not be calculated as  
  //the hyperbolic sine. 
  document.write(Math.sinh(1 + 2i)); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

Apart from integer, nothing is agreed as the function parameter hence why the string here as the parameter gives NaN i.e. not a number.

```
<script> 
  // Any string value as the parameter of the function 
  // gives NaN i.e, not a number 
  // because only number can be used as the parameters. 
  document.write(Math.sinh("geeksforgeeks") + "<br>"); 
  document.write(Math.sinh("gfg")); 
</script> 
```

Output:

```
NaN
NaN
```

**Application:**

The practical application is that we use Math.sinh() method in JavaScript whenever we need to determine the value of a number's hyperbolic sine.

Example 1:

```
<script> 
  // Printing hyperbolic sine of some numbers from 0 to 9 
  // taken as parameter of Math.sinh() function. 
  for (i = 0; i < 10; i++) { 
    document.write(Math.sinh(i) + "<br>"); 
  } 
</script> 
```

Output:

```
0
1.1752011936438014
3.626860407847019
10.017874927409903
27.28991719712775
74.20321057778875
201.71315737027922
548.3161232732465
1490.4788257895502
4051.54190208279
```

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari