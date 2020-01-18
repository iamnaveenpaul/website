---
image: "/assets/default-social-image.png"
title: JavaScript Math.log2() function
categories: JavaScript-math
---

The Math.log10() is a JavaScript built-in function which provides any number's value of base 2 logarithms.

**Syntax:**

`Math.log2(p)`

**Parameters:**

This method recognizes a single paratameter p which is any number to be determined using base 2 logarithms.

**Returns:**

This returns any number with the value of base 2 logarithms.

Examples:

```
Input : Math.log2(5)
Output: 2.321928094887362
```

Explanation:

The value of the base 2 logarithms of number 5 is here shown output as 2.321928094887362.

```
Input : Math.log2(10)
Output:3.321928094887362
```

Example 1:

```
<script> 
  // Different numbers are being taken 
  // as the parameter of the function. 
  document.write(Math.log2(1000) + "<br>"); 
  document.write(Math.log2(12) + "<br>"); 
  document.write(Math.log2(26) + "<br>"); 
  document.write(Math.log2(5)); 
</script> 
```

Output:

```
9.965784284662087
3.584962500721156
4.700439718141092
2.321928094887362
```

Example 2:

```
<script> 
  // Taken parameter from 1 to 19 incremented by 3. 
  for (i = 1; i < 20; i += 3) { 
      document.write(Math.log2(i) + "<br>"); 
  } 
</script> 
```

Output:

```
0
2
2.807354922057604
3.321928094887362
3.700439718141092
4
4.247927513443585
```

**Errors and exceptions:**

Parameters should always be a number for such a method or else it will return NaN i.e., not a number if its parameter is treated as a string.

Example 1:

```
<script> 
  // Parameters for this function should always be a 
  // number otherwise it return NaN i.e, not a number 
  // when its parameter taken as string. 
  document.write(Math.log2("gfg")); 
</script> 
```

Output:

`NaN`

Example 2:

This function provides error if its parameter is taken as complex number since it takes as parameter as just an integer value.

```
<script> 
  // Parametes can never be a complex number because 
  // it accept only integer value as the parameter. 
  documnet.write(Math.log2(1 + 2i)); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

**Application:**

Whenever we need the value of any number of base 2 logarithms we take help of this function. Its importance is required often times in math problem.

Example 1:

```
<script> 
  // taking parameter as number 14 and  
  //calculated in the form of function. 
  function value_of_base_2_logarithms_of_any_number() 
  { 
    return Math.log2(14); 
  } 
  document.write(value_of_base_2_logarithms_of_any_number()); 
</script> 
```

Output:

`3.807354922057604`

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari