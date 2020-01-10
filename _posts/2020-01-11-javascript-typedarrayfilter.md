---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.filter()
categories: JavaScript-typedArray
---

The typedArray.filter() is a built-in feature in javascript that is used to create a new typedArray with the elements that satisfy the test defined by the given method.

**Syntax:**

`typedarray.filter(callback)`

**Parameters:**

It takes the function "callback" parameter to check each element of the typedArray that is satisfied with the condition. Callback takes three parameters indicated below.

* **element:** It's the element's value.
* **index:** It's the element's value index.
* **array:** It's the array which are traversed.

**Return value:**

It returns with the elements that satisfy the test a new typedArray.

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
   const D = new Int8Array([ -10, 20, 30, 40, -50 ]); 
  
   // Calling filter() function to check condition 
   // provided by its parameter 
   const a = A.filter(isNegative); 
   const b = B.filter(isNegative); 
   const c = C.filter(isNegative); 
   const d = D.filter(isNegative); 
  
   // Printing the filtered typedArray 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d); 
     
</script> 
```

Output:

```
-10,-30,-50
-30,-50
-10,-30
-10,-50
```