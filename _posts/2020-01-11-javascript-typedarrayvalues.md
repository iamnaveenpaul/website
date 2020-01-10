---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.values()
categories: JavaScript-typedArray
---

The typedArray.values() is a JavaScript built-in function that is used to get the specified value of the typedArray() contents.

**Syntax:**

`typedArray.values()`

**Parameters:**

This acknowledges no parameters.

**Return value:**

It returns the given typedArray object's specified value.

Code #1:

```
<script> 
  
   // Constructing a new typedArray Uint8Array() with some value. 
   const A = new Uint8Array([ 5, 10, 15, 20, 25, 30 ]); 
  
   // Calling typedArray.values() function. 
   const B = A.values(); 
  
   // Shifting array iterator to next element 
   // iterator assigned to 10 
   B.next(); 
     
   // iterator assigned to 15 
   B.next(); 
     
   // iterator assigned to 20 
   B.next(); 
  
   // Printing value 20  
   document.write(B.next().value); 
     
</script> 
```

Output:

`20`

Code #2:

```
<script> 
  
   // Constructing a new typedArray Uint8Array() with some value. 
   const A = new Uint8Array([5, 10, 15, 20, 25, 30]); 
  
   // Calling typedArray.values() function. 
   const B = A.values(); 
  
   // Shifting array iterator to next element 
   // iterator assigned to 10 
   B.next(); 
     
   // iterator assigned to 15 
   B.next(); 
     
   // iterator assigned to 20 
   B.next(); 
     
   // iterator assigned to 25 
   B.next(); 
     
   // iterator assigned to 30 
   B.next(); 
     
   // Now iterator go beyond the index 
   B.next(); 
  
   document.write(B.next().value);  
     
</script> 
```

Output:

`undefined`

Output is undefined here because the upper bound is crossed by the array iterator.