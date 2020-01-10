---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.findIndex()
categories: JavaScript-typedArray
---

The typedArray.findIndex() is a built-in function in JavaScript that is used to return an index in the tyedArray if the value fulfills the function's condition, or else it reverts -1.

Syntax:

`typedarray.findIndex(callback)`

**Parameters:**

It takes the function "callback" parameter to verify each element of the typedArray that is content with the condition. The function Callback accepts three parameters defined below.

* **element:** It's the element's value.
* **index:** It's the element's index.
* **array:** It's the array being traversed.

**Return value:**

If the elements met the condition offered by the function, it reverts an index in the array, or else it will revert -1.

Example:

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
  
   // Calling findIndex() function to check condition 
   // provided by its parameter 
   const a = A.findIndex(isNegative); 
   const b = B.findIndex(isNegative); 
   const c = C.findIndex(isNegative); 
   const d = D.findIndex(isNegative); 
  
   // Printing the indexes typedArray 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d); 
  
</script> 
```

Output:

```
0
2
0
-1
```