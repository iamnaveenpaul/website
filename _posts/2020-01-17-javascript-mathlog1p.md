---
image: "/assets/default-social-image.png"
title: JavaScript Math.log1p()
categories: JavaScript-math
---

The Math.log1p() is an built-in function in JavaScript that gives the natural logarithm value (of base e, where e is an approximately equivalent to 2.718 as value) the 1 + p number.

**Syntax:**

`Math.log1p(1 + p)`

**Parameters:**

In parameter 1+p, p is any number which is determined with the natural logarithm of base e.

**Returns:**

It returns the base e value of any number logarithm added with 1.

Examples:

```
Input  : Math.log1p(5)
Output : 1.791759469228055
```

Explanation:

The natural logarithm value of number 5 here is 1.791759469228055 as shown in the output.

```
Input  : Math.log1p(10)
Output : 2.3978952727983707
```

Example 1:

```
<script> 
  
// Different numbers are being taken 
// as the parameter of the function. 
document.write(Math.log1p(1000) + "<br>"); 
document.write(Math.log1p(12) + "<br>"); 
document.write(Math.log1p(26) + "<br>"); 
document.write(Math.log1p(5)); 
  
</script> 
```

Output:

```
6.90875477931522
2.5649493574615367
3.295836866004329
1.791759469228055
```

Example 2:

```
<script> 
  
// Taken parameter from 1 to 19 incremented by 3. 
for (i = 1; i < 20; i += 3) 
{ 
    document.write(Math.log1p(i) + "<br>"); 
} 
  
</script> 
```

Output:

```
0.6931471805599453
1.6094379124341003
2.0794415416798357
2.3978952727983707
2.639057329615259
2.833213344056216
2.995732273553991
```

**Errors and exceptions:**

Parameters must always be a number for this method otherwise it will return NaN i.e. not a number, when taken as a string.

Example 1:

```
<script> 
  
    // Parameters for this function should always be a 
    // number otherwise it return NaN i.e, not a number 
    // when its parameter taken as string. 
    document.write(Math.log1p("gfg")); 
  
</script> 
```

Output:

`NaN`

Example 2:

This function provides error when it takes the parameter as a complex number because it only recognizes the integer value as the parameter.

```
<script> 
  
    // Parameters can never be a complex number because 
    // it accept only integer value as the parameter. 
    document.write(Math.log1p(1 + 2i)); 
  
</script> 
```

Output:

`Error: Invalid or unexpected token`

Example 3:

This function returns NaN, if the parameter is less than -1 since number should be any positive number i.e. > 0.

```
<script> 
  
    // This function return NaN i.e, not a number 
    // if the parameter is less 
    // than -1 because number should be 
    // any positive number i.e, greater then 0. 
    document.write(Math.log1p(-2)); 
  
</script> 
```

Output:

`NaN`

**Application:**

If we have to calculate the normal logarithm value of 1 + p number anytime, we consider this method. The value is used in math problems often.

Example 1:

```
<script> 
  
    // taking parameter as number 14 and calculated 
    // in the form of function. 
    function value_of_base_e_logarithms_of_any_number() { 
        return Math.log10(14); 
    } document.write(value_of_base_e_logarithms_of_any_number()); 
  
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