---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.reduce()
categories: JavaScript-typedArray
---

The typedArray.reduce() is a built-in function in JavaScript that reduces each element of the typedArray to a single value from left to right.

**Syntax:**

`typedArray.reduce(callback)`

**Parameters:**

It accepts a callback function parameter that recognizes those parameters defined below.

* **previousValue:** It is the value that was previously returned.
* **currentValue:** It is the current element in the typedArray being processed.

**Return value:**

It returns the reduce() function result.

Code #1:

```
<script> 
    
  // Creating some typedArray 
  const A = new Uint8Array([ 1, 2, 3, 4]); 
  const B = new Uint8Array([5, 6, 7]); 
  const C = new Uint8Array([1, 3, 5]); 
  const D = new Uint8Array([2, 4, 6, 8]); 
  
  // Calling sum() function  
  function sum(previousValue, currentValue) { 
  return previousValue + currentValue; 
  } 
  
  // Printing reduced value of the given typedArray 
  document.write(A.reduce(sum) +"<br>"); 
  document.write(B.reduce(sum) +"<br>"); 
  document.write(C.reduce(sum) +"<br>"); 
  document.write(D.reduce(sum)); 
     
     
</script> 
```

Output:

```
10
18
9
20
```