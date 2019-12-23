---
image: "/assets/default-social-image.png"
title: JavaScript uneval() with Examples
categories: JavaScript-functions
---

uneval() is a JavaScript built-in function that is used to construct a string representation of an object's source code.

**Syntax:**

`uneval(object)`

Parameters: It accepts an object that can be an expression or statement in JavaScript.

Return Value: returns a string that describes the given object's source code.

Code to show the working of this function:

**Code #1:**

If the amount is passed to uneval() function, then a string with the passed object value will be returned by the function.

```
<script> 
  
  var obj = 2; 
  document.write(eval(obj)); 
  
</script> 
```

Output:

`2`

**Code #2:**

If the char is passed to uneval(), then a string with the passed object value will be returned by the function.

```
<script> 
  
  var obj = '2'; 
  document.write(uneval(obj)); 
  
</script> 
```

Output:

`"2"`

**Code #3:**

If the number is passed to uneval() then a string with the passed object value will be returned by the function.

```
<script> 
  
  var obj = uneval(function func() { return 'ThisIsMyWorld'; }); 
  var func1 = eval(obj); 
  document.write(func1()); 
  
</script> 
```

Output:

`ThisIsMyWorld`

**Difference between eval() and uneval() functions:**

The uneval() function returns a specified object's source while the eval() function evaluates the source code in different memory region.

Note: The code above will only function in the web browser of Firefox.