---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.entries()
categories: JavaScript-typedArray
---

The typedArray.entries() is a JavaScript built-in function that gives a new iterator array object containing the key and value pairs of the given typedArray object.

**Syntax:**

`typedArray.entries()`

**Parameter:**

This acknowledges no parameters.

**Return value:**

It returns a new iterator array object that contains the key and value pairs of the specified array object.

Code #1:

```
<script> 
  
    // Creating a typedArray Uint8Array() with some elements 
    const uint8 = new Uint8Array([ 5, 10, 15, 20, 25, 30 ]); 
  
    // Calling entries() function 
    A = uint8.entries(); 
  
    // Shifting array iterator to next element one by one 
    // Iterator assigned to 10 
    A.next(); 
      
    // Iterator assigned to 15 
    A.next(); 
      
    document.write(A.next().value); 
  
</script> 
```

Output:

`2, 15`

Here 2 is the element 15 index.

Code #2:

```
<script> 
  
    // Creating a typedArray Uint8Array() with some elements 
    const uint8 = new Uint8Array([ 5, 10, 15, 20, 25 ]); 
  
   // Calling entries() function 
   A = uint8.entries(); 
  
   // Shifting array iterator to next element one by one 
   // Iterator assigned to 10 
   A.next(); 
     
   // Iterator assigned to 15 
   A.next(); 
     
   // Iterator assigned to 20 
   A.next(); 
     
   // Iterator assigned to 25 
   A.next(); 
     
   // Iterator went out of index 
   A.next(); 
   document.write(A.next().value); 
     
</script> 
```

Output:

`undefined`

The output here is undefined as the iterator exceeds the upper bound.