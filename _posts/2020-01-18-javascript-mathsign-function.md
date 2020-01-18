---
image: "/assets/default-social-image.png"
title: Javascript Math.sign() Function
categories: JavaScript-math
---

The Math.sign() is an in-built method of JavaScript which is used for determining a number's sign, specifying whether the defined number is negative or positive.

**Syntax:**

`Math.sign(number)`

**Parameters:**

This function recognizes a single number for parameters that signifies the number that you want to know about it's sign.

**Return Value:**

The function Math.sign() returns five values:

When the passed argument is a positive number, it returns 1.
When the passed argument is a negative number, it returns -1.
When the passed argument is a positive zero, it returns 0.
When the passed argument is a negative zero, it returns -0.
When none of the aforementioned situations suit, then NaN is returned.

Examples:

```
Input  : Math.sign(2)
Output : 1
```
     
```
Input  : Math.sign(-2)
Output : -1
```

```
Input  : Math.sign(0)
Output : 0
```

```
Input  : Math.sign(-0)
Output : -0
```

```
Input  : Math.sign(haa)
Output  : NaN
```

Example 1:

If the passed number as an argument is positive.

```
<script type="text/javascript"> 
   document.write(Math.sign(2));           
</script> 
```

Output:

`1`

Example 2:

If the passed number as an argument is negative.

```
<script type="text/javascript"> 
   document.write(Math.sign(-2));           
</script> 
```

Output:

`-1`

Example 3:

If the passed argument is positive zero.

```
<script type="text/javascript"> 
   document.write(Math.sign(0));           
</script> 
```

Output:

`0`

Example 4:

If the passed argument is negative zero.
   
```
<script type="text/javascript"> 
    document.write(Math.sign(-0));           
 </script> 
```

Output:

`-0`

Example 5:

If the passed as an argument is an invalid number.

```
<script type="text/javascript"> 
   document.write(Math.sign(haa));           
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