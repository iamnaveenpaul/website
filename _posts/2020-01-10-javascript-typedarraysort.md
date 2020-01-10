---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.sort()
categories: JavaScript-typedArray
---

The typedArray.sort() is a built-in function in JavaScript that is used to sort the provided typedArray elements and return the new typedArray with the sorted elements.

**Syntax:**

`typedArray.sort();`

**Parameter:**

This acknowledges no parameters.

**Return value:**

It returns with the sorted elements the new typedArray.

Example:

```
<script> 
  
// Creating some typedArrays with some elements 
const A = new Uint8Array([ 5, 9, 1, 0, 45, 2 ]); 
const B = new Uint8Array([ 22, 9, 1, 20 ]); 
const C = new Uint8Array([ 5, 9, 0, 3, 1 ]); 
const D = new Uint8Array([ 1, 3, 100, 42, 4 ]); 
  
// Calling sort() function on the above typedArray 
a = A.sort(); 
b = B.sort(); 
c = C.sort(); 
d = D.sort(); 
  
// Printing the sorted typedArray 
document.write(a + "<br>"); 
document.write(b + "<br>"); 
document.write(c + "<br>"); 
document.write(d + "<br>"); 
  
</script> 
```

Output:

```
0, 1, 2, 5, 9, 45
1, 9, 20, 22
0, 1, 3, 5, 9
1, 3, 4, 42, 100
```