---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.set()
categories: JavaScript-typedArray
---

The typedArray.set() is a JavaScript built-in function that is used to store a number of values in the given typedArray.

**Syntax:**

`typedArray.set(typedArray, offset)`

**Parameters:**

This acknowledges two parameters indicated below:

* **typedarray:** This is the array of source.
* **offset:** This is optional and you can start setting the values in the typedArray. The initial values is zero (0).

**Return value:**

It reverts the newly formed typedArray.

Example:

```
<script> 
  
  // Creating some buffers with sizes in bytes 
  const buf1 = new ArrayBuffer(8); 
  const buf2 = new ArrayBuffer(12); 
  const buf3 = new ArrayBuffer(16); 
  
  // Creating some typedArray 
  const A = new Uint8Array(buf1); 
  const B = new Uint8Array(buf2); 
  const C = new Uint8Array(buf3); 
  
  // Coping the values into the array 
  // starting at index 3, 4, 5 
  A.set([ 1, 2, 3, 4 ], 3); 
  B.set([ 1, 2, 3, 5, 6 ], 4); 
  C.set([ 1, 2 ], 5); 
  
  // Priniting modified values 
  document.write(A +"<br>"); 
  document.write(B +"<br>"); 
  document.write(C); 
    
</script> 
```

Output:

```
0,0,0,1,2,3,4,0
0,0,0,0,1,2,3,5,6,0,0,0
0,0,0,0,0,1,2,0,0,0,0,0,0,0,0,0
```