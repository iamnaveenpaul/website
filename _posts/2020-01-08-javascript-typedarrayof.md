---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.of()
categories: JavaScript-typedArray
---

The typedArray.of() is a JavaScript built-in function that is used to build a new typedArray with a number of parameters that are variable.

**Syntax:**

`TypedArray.of(element0, element1, ......)`

**Parameters:**

It recognizes parameters of various elements that will be generated with typedArray.

**Return value:**

It returns the new instance of typedArray.

Example:

```
<script> 
  
    // Printing the new typedArray with the given elements with 
    // the parameters of typedArray.of() function. 
    document.write(Uint8Array.of(5, 9, 1, 0, 45, 2) + "<br>"); 
    document.write(Uint8Array.of(22, 9, 1, 20) + "<br>"); 
    document.write(Uint8Array.of(5, 9, 0, 3, 1) + "<br>"); 
    document.write(Uint8Array.of(undefined) + "<br>"); 
  
</script> 
```

Output:

```
5, 9, 1, 0, 45, 2
22, 9, 1, 20
5, 9, 0, 3, 1
0
```