---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.keys()
categories: JavaScript-typedArray
---

The typedArray.keys() is a built-in function in JavaScript that is used to return a new array iterator that contains the keys for each index of the typedArray elements.

**Syntax:**

`typedArray.keys()`

**Parameter:**

This function does not accept the parameter of anything.

**Return value:**

It returns a new iterator array object that contains the keys for each index of the typedArray elements.

Example:

```
<script> 
  
  // Creating some typedArrays 
  const A = new Uint8Array([1, 2, 3, 4, 5]); 
  const B = new Uint8Array([5, 10, 15, 20]); 
  const C = new Uint8Array([0, 2, 4, 6, ,8, 10]); 
  const D = new Uint8Array([1, 3, 5, 7, 9]); 
   
   // Calling keys() function 
   a = A.keys() 
   document.write(a.next().value +"<br>"); 
     
   b = B.keys() 
   b.next(); 
   document.write(b.next().value +"<br>"); 
     
   c = C.keys() 
   c.next(); 
   c.next(); 
   document.write(c.next().value +"<br>"); 
     
   d = D.keys() 
   d.next(); 
   d.next(); 
   d.next(); 
   document.write(d.next().value +"<br>"); 
      
</script> 
```

Output:

```
0
1
2
3
```