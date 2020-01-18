---
image: "/assets/default-social-image.png"
title: JavaScript Math.log10() function
categories: JavaScript-math
---

The Math.log10() is a JavaScript built-in function which provides any number to the value of base 10 logarithms.

**Syntax:**

`Math.log10(p)`

**Parameters:**

This function accepts a single parameter p which is any number whose base 10 is to be calculated using logarithms.

**Returns:**

It returns every number's base 10 logarithm value.

Examples:

```
Input : Math.log10(5)
Output: 0.6989700043360189
```

**Explanation:**

The value of base 10 logarithms of number 5 is as shown output 0.6989700043360189.

```
Input : Math.log10(10)
Output:1
```

Example 1:

```
<script> 
  // Different numbers are being taken 
  // as the parameter of the function. 
  document.write(Math.log10(1000) + "<br>"); 
  document.write(Math.log10(12) + "<br>"); 
  document.write(Math.log10(26) + "<br>"); 
  document.write(Math.log10(5)); 
</script> 
```

Output:

```
3
1.0791812460476249
1.414973347970818
0.6989700043360189
```

Example 2:

```
<script> 
  // Taken parameter from 1 to 19 incremented by 3. 
  for (i = 1; i < 20; i += 3) { 
      document.write(Math.log10(i) + "<br>"); 
  } 
</script> 
```

Output:

```
0
0.6020599913279624
0.8450980400142568
1
1.1139433523068367
1.2041199826559248
1.2787536009528289
```

**Errors and exceptions:**

Parameters should always be a number for this function otherwise it will return NaN i.e., not a number when its parameter is taken as a string.

Example 1:

```
<script> 
  // Parameters for this function should always be a 
  // number otherwise it return NaN i.e, not a number 
  // when its parameter taken as string. 
  document.write(Math.log10("gfg")); 
<script> 
```

Output:

`NaN`

Example 2:

This function provides error once its parameter is took a complex number as it takes as parameter only the integer value.

```
<script> 
  // Parametes can never be a complex number because 
  // it accept only integer value as the parameter. 
  document.write(Math.log10(1 + 2i)); 
</script>
```

Output:

`Error: Invalid or unexpected token`

**Application:**

If we need the value of base 10 logarithms of any number, we take the help of this method. In math problems, its importance is required often.

Example 1:

```
<script> 
  // taking parameter as number 14 and  
  //calculated in the form of function. 
  function value_of_base_10_logarithms_of_any_number() 
  { 
      return Math.log10(14); 
  } 
  document.write(value_of_base_10_logarithms_of_any_number()); 
</script> 
```

Output:

`1.146128035678238`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari