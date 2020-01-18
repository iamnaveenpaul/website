---
image: "/assets/default-social-image.png"
categories: JavaScript-math
title: JavaScript Math.E() function
---

The Math.E() is a built-in function in JavaScript that is used to get the ep value, where p is any integer. The number e is a mathematical constant which has an approximate value of 2.718. It was the Swiss mathematician Jacob Bernoulli who invented this. Also the number is called the Euler's number.

**Syntax:**

`Math.exp(p)`

**Parameter:**

This function recognizes any number for any single parameter p.

**Return Value:**

It returns the value of ep, where p as parameter is any given number.

Example:

```
Input  : Math.exp(0)
Output : 1
```

**Explanation:**

Here the value of the parameter p if used 0, the value of ep is 1.

```
Input  : Math.exp(2)
Output : 7.38905609893065
```

Explanation:

Here the value of the parameter p is 2, so its value is 7.38905609893065 after placing the value 2 instead of p in ep.

Example 1:

```
<script> 
  // Here different values is being taken as 
  // as parameter of Math.exp() function. 
  document.write(Math.exp(0) + "<br>"); 
  document.write(Math.exp(1) + "<br>"); 
  document.write(Math.exp(2) + "<br>"); 
  document.write(Math.exp(-1) + "<br>"); 
  document.write(Math.exp(-7) + "<br>"); 
  document.write(Math.exp(10) + "<br>"); 
  document.write(Math.exp(1.2)); 
</script> 
```

Output:

```
1
2.718281828459045
7.38905609893065
0.36787944117144233
0.0009118819655545162
22026.465794806718
3.3201169227365472
```

Example 2:

The parameter here should be a number else it will give error or NaN i.e., not a number.

```
<script> 
  // Here alphabet parameter give error. 
  document.write(Math.exp(a)); 
</script> 
```

Output:

`Error: a is not defined`

```
<script> 
  // Here parameter as a string give NaN. 
  document.write(Math.exp("gfg")); 
</script> 
```

Output:

`NaN`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari