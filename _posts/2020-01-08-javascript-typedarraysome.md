---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.some()
categories: JavaScript-typedArray
---

The typedArray.some() is a built-in feature in JavaScript that is used to verify whether certain elements of the typedArray fulfill the test performed by the function provided.

Syntax:

`typedarray.some(callback)`

**Parameters:**

It takes the callback function parameter and this callback function takes three parameters defined below.

**value:** This takes the existing element's value.
**index:** This takes the index of the current element that the tyepdArray is heading through.
**array:** This is the typedArray required.

**Return value:**

This returns true if all the elements are transferred by the callback function, otherwise it will return false.

Example:

```
<script> 
  
  // Creating isNegative() function 
  function isNegative(element, index, array) 
  { 
    return element < 0; 
  } 
  
  // Creating some typedArrays containing different  
  // positive and negative values 
  const A = new Int8Array([-5, 10, -15, 20, -25 ]); 
  const B = new Int8Array([5, 10, 15, 20, 25 ]); 
  const C = new Int8Array([-10, -20, -30, -40, -50 ]); 
  const D = new Int8Array([0, 0, 0, 0 ]); 
  
  // Printing true or false on checking 
  document.write(A.some(isNegative) +"<br>"); 
  document.write(B.some(isNegative) +"<br>"); 
  document.write(C.some(isNegative) +"<br>"); 
  document.write(D.some(isNegative)); 
    
</script> 
```

Output:

```
true
false
true
false
```

Here output is true because there are negative elements in the typedArray A and C, B and D typedArray have positive elements, which is why the output is false.