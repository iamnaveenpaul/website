---
image: "/assets/default-social-image.png"
title: JavaScript Math.clz32() function
categories: JavaScript-math
---

Math.clz32() is a "Count Leading Zeroes 32" built-in method in JavaScript. This function is used to determine the number of leading zero bits found in a number's 32-bit representation.

**Syntax:**

`Math.clz32(p)`

**Parameter:**

This method takes a single parameter p, a number to which it can figure out the number of leading zero bits contained in its 32-bit representation.

**Returns:**

It returns the number of leading zero bits in 32-bit numeral representation.

Examples:

```
Input  : Math.clz32(10)
Output : 28
```

**Explanation:**

Here you can see the number 10 in 32-bit as shown below:

`00000000000000000000000000001010`

From the description above, we see that there are a total of 28 zero bits that lead 1010 i.e. 4 bit decimal number 10. This is why output here becomes 28 as the leading zero bits is 28.

```
Input  : Math.clz32(64)
Output :25 
```

Example 1:

```
<script> 
  // Here different number is being taken as parameter for 
  // Math.clz32() function. 
  document.write(Math.clz32(1) + "<br>"); 
  document.write(Math.clz32(8) + "<br>"); 
  document.write(Math.clz32(32) + "<br>"); 
  document.write(Math.clz32(64) + "<br>"); 
  document.write(Math.clz32(772) + "<br>"); 
</script> 
```

Output:

```
31
28
26
25
22
```

Example 2:

Errors and Exceptions: this is an error scenario because it is not possible to convert a complex number into 32-bit binary representation which can only be translated to integer values.

```
<script> 
  // complex number can not be converted into 
  // 32-bit binary representation. 
  document.write(Math.clz32(1+2i)); 
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

It is an exceptional case that this can be viewed as a string parameter and allows internally zero then it becomes probable else an error should be returned.

```
<script> 
  // Any string behave exceptionally and give leading 
  // 32 zero bit in its 32-bit binary representation 
  // still any string can not be converted into  
  // 32-bit binary representation. 
  document.write(Math.clz32("geeksforgeeks") + "<br>"); 
  document.write(Math.clz32("gfg")); 
</script> 
```

Output:

```
32
32
```

**Application:**

Here Math.clz32() function has many implementations because whenever we need to get the number of leading zero bits existing in the 32-bit representation of a number, and to that instance in JavaScript we take advantage of this function.

Example:

```
<script> 
  // Here different numbers are being taken as 
  // parameter from 0 to 9 for Math.clz32() function. 
  for (i = 0; i < 10; i++) 
  {  
      document.write(Math.clz32(i) + "<br>");  
  } 
</script> 
```

Output:

```
32
31
30
30
29
29
29
29
28
28
```

**Supported Browsers:**

The browsers provided with the function JavaScript Math.clz32() are described below:

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari