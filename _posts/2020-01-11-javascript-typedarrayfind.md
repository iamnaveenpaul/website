---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.find()
categories: JavaScript-typedArray
---

The typedArray.find() is a built-in function in JavaScript that is used to return a value in the typedArray, if the value meets the condition specified in the method, otherwise it returns undefined.

**Syntax:**

`typedArray.find(callback)`

**Parameters:**

It involves the function "callback" parameter to validate each element of the typedArray that is satisfied with the condition. The function Callback takes three parameters described below.

* **element:** It's the element's value.
* **index:** It's the element's index.
* **array:** This is the traversed array.

**Return value:**

If the elements meets the condition supplied by the function, it returns an array value, or else it returns undefined.

Exapmple:

```
<script> 
  
   // Calling isNegative function to check 
   // elements of the typedArray 
   function isNegative(element, index, array) 
   { 
    return element < 0; 
   } 
  
   // Created some typedArrays. 
   const A = new Int8Array([ -10, 20, -30, 40, -50 ]); 
   const B = new Int8Array([ 10, 20, -30, 40, -50 ]); 
   const C = new Int8Array([ -10, 20, -30, 40, 50 ]); 
   const D = new Int8Array([ 10, 20, 30, 40, 50 ]); 
  
   // Calling find() function to check condition 
   // provided by its parameter 
   const a = A.find(isNegative); 
   const b = B.find(isNegative); 
   const c = C.find(isNegative); 
   const d = D.find(isNegative); 
  
   // Printing the finded typedArray 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d); 
  
</script> 
```

Output:

```
-10
-30
-10
undefined
```