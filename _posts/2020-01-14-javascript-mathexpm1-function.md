---
image: "/assets/default-social-image.png"
title: JavaScript Math.expm1() function
categories: JavaScript-math
---

Math.expm1() is a JavaScript built-in function which is used to get the value of ep-1, where p is any specified number. The e is a mathematical constant which has an approximate value of 2.718. It was the Swiss mathematician Jacob Bernoulli who discovered this. Also that number is called the Euler's constant.

**Syntax:**

`Math.expm1(p)`

**Parameter:**

This method acknowledges a single parameter p, which is the value and can be of any value.

**Returns:**

It returns the value of ep-1, where p is parameter of any given number.

Example:

```
Input  :Math.expm1(0)
Output : 0
```

Explanation:

Now the value of the parameter p is 0, So after placing the value 0 in ep-1 instead of p, its value is 0.

Example

```
<script> 
  // Here different values is being taken as 
  // as parameter of Math.expm1() function. 
  document.write(Math.expm1(0) + "<br>"); 
  document.write(Math.expm1(1) + "<br>"); 
  document.write(Math.expm1(2) + "<br>"); 
  document.write(Math.expm1(-1) + "<br>"); 
  document.write(Math.expm1(5) + "<br>"); 
  document.write(Math.expm1(2.2) + "<br>"); 
  document.write(Math.expm1(-3.2) + "<br>"); 
</script> 
```

Output:

```
 0
 1.718281828459045
 6.38905609893065
-0.6321205588285577
 147.4131591025766
 8.025013499434122
-0.9592377960216338
```

Example 2:

Exception, the parameter here should be a number else it will show error or NaN, i.e., not a number.

```
<script> 
  // Here alphabet parameter give error. 
  document.write(Math.expm1(C)); 
</script> 
```

Output:

`Error: C is not defined`

Example 3:

```
<script> 
  // Here parameter as a string give NaN. 
  document.write(Math.expm1("geeksforgeeks")); 
</script> 
```

Output:

`NaN`

**Application:**

In JavaScript, anytime we need to calculate the value of ep-1, in which p is any specified number each time we use the Math.expm1() method.

Example:

```
<script> 
  // Here different numbers are being taken as parameter 
  // from 0 to 9 for Math.expm1() function. 
  for (i = 0; i < 10; i++) { 
      console.log(Math.expm1(i)+ "<br>"); 
  } 
</script> 
```

Output:

```
 0
 1.718281828459045
 6.38905609893065
 19.085536923187668
 53.598150033144236
 147.4131591025766
 402.4287934927351
 1095.6331584284585
 2979.9579870417283
 8102.083927575384
```

**Supported Browsers:**

The browsers supported with the method JavaScript Math.expm1() are:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari