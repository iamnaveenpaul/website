---
image: "/assets/default-social-image.png"
title: JavaScript Math.LOG10E property
categories: JavaScript-math
---

The Math.LOG10E is a JavaScript property which is essentially used to calculate the base 10 logarithm value of e, where e is an irrational and transcendental number roughly 2.718 as its value.

Syntax:

`Math.LOG10E;`

**Parameters:**

Nothing is as a parameter here, as Math.LOG10E is not a function but a property.

**Return Values:**

This simply returns the logarithm value of base 10 of e.

Example:

```
Input  : Math.LOG10E
Output : 0.4342944819032518
```

**Explanation:**

The value of base 10 logarithm of e is essentially shown in the output here.

Example 1:

```
<script> 
  // Here value of Math.LOG10E is printed. 
  document.write(Math.LOG10E); 
</script> 
```

Output:

`0.4342944819032518`

Example 2:

Value of base 10 logarithm of e can be written as in function form as:

```
<script> 
  // function is being called. 
  function get_Value_of_base_10_lagarithm_of_e() 
  { 
      return Math.LOG10E; 
  } 
  // function is calling. 
  document.write(get_Value_of_base_10_lagarithm_of_e()); 
</script> 
```

Output:

`0.4342944819032518`

**Errors and Exceptions:**

Here we assume Math.LOG10E as a parameter but it is simply a property which is why error is shown as output.

Example:

```
<script> 
  // Here we consider Math.LOG10E as a function  
  //but in actual it is a property that is why 
  // error as output is being shown. 
  document.write(Math.LOG10E(12)); 
</script> 
```

Output:

`Error: Math.LOG10E is not a function`

**Application:**

We take the help of this property whenever we need to find the value of base 10 logarithms of the e anytime. It's required a lot in math problems.

Example:

```
<script> 
  // Value of Math.LOG10E is printed. 
  document.write(Math.LOG10E); 
</script> 
```

Output:

`0.4342944819032518`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari