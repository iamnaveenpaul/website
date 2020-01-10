---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.join()
categories: JavaScript-typedArray
---

The typedArray.join() is a JavaScript built-in feature that is used to combine all the elements of the specified typedArray onto a string.

**Syntax:**

`typedArray.join(separator);`

**Parameters:**

It acknowledges a "separator" parameter that is used to separate the typedArray elements. It is optional and the predefined one is a comma (',').

**Return value:** It reverts a string that contains all the elements that are formed together.

Example:

```
<script> 
  
  // Creating some typedArrays 
  const A = new Uint8Array([1, 2, 3, 4, 5]); 
  const B = new Uint8Array([5, 10, 15, 20]); 
  const C = new Uint8Array([0, 2, 4, 6, ,8, 10]); 
  const D = new Uint8Array([1, 3, 5, 7, 9]); 
   
   // Calling join() function 
   a = A.join() 
   b = B.join('/') 
   c = C.join('+') 
   d = D.join('&') 
   
   // Printing new strings with joined elements 
   document.write(a +"<br>"); 
   document.write(b +"<br>"); 
   document.write(c +"<br>"); 
   document.write(d); 
      
</script> 
```

Output:

```
1,2,3,4,5
5/10/15/20
0+2+4+6+0+8+10
1&3&5&7&9
```