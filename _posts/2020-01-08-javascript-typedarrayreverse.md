---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.reverse()
categories: JavaScript-typedArray
---

The typedArray.reverse() is a built-in function in JavaScript that is used to reverse the typedArray elements that are provided, i.e. the first element becomes the last and vice versa.

**Syntax:**

`typedArray.reverse();`

**Parameter:**

This acknowledges no parameters.

**Return value:**

This returns the new typedArray reversed.

Example:

```
<script> 
  
    // Creating some typedArrays with some elements 
    const A = new Uint8Array([ 1, 2, 3, 4, 5, 6 ]); 
const B = new Uint8Array([ 5, 10, 15, 20 ]); 
const C = new Uint8Array([ 2, 4, 6, 8, 10 ]); 
const D = new Uint8Array([ 1, 3, 5, 7 ]); 
const E = new Uint8Array(); 
  
// Calling reverse() function on the above typedArray 
a = A.reverse(); 
b = B.reverse(); 
c = C.reverse(); 
d = D.reverse(); 
e = E.reverse(); 
  
// Printing the reversed typedArray 
document.write(a + "<br>"); 
document.write(b + "<br>"); 
document.write(c + "<br>"); 
document.write(d + "<br>"); 
document.write(e); 
  
</script> 
```

Output:

```
6, 5, 4, 3, 2, 1
20, 15, 10, 5
10, 8, 6, 4, 2
7, 5, 3, 1
```