---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.reduceRight()
categories: JavaScript-typedArray
---

The typedArray.reduceRight() is a built-in JavaScript function that reduces each element of the typedArray from right to left to a single value.

Syntax:

`typedArray.reduceRight(callback)`

**Parameters:**

It accepts a callback function parameter that accepts certain parameters stated below.

* **previousValue:** It is the value that was previously returned.
* **currentValue:** It is the current element in the typedArray being processed.

**Return value:**

It returns the output of the function reduRight().

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
  document.write(A.reduceRight(sum) +"<br>"); 
  document.write(B.reduceRight(sum) +"<br>"); 
  document.write(C.reduceRight(sum) +"<br>"); 
  document.write(D.reduceRight(sum)); 
     
     
</script> 
```

Output:

```
10
18
9
20
```