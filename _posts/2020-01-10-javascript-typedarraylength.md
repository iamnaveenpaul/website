---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.length()
categories: JavaScript-typedArray
---

The typedArray.length is a JavaScript built-in property that is used to return the specified typedArray length.

**Syntax:**

`typedArray.length`

**Parameters:**

It accepts no parameters because it is not a function but a property.

**Return value:**

It returns the typedArray's length.

Code #1:

```
<script> 
  
  // Creating a typedArray with some elements 
  var A = new Uint8Array([5, 10, 15, 15, 5, 20, 10]); 
  var B = new Uint8Array([5, 10]); 
  var C = new Uint8Array([5, 10, 15]); 
  var D = new Uint8Array([5, 10, 15, 15, 5]); 
  var E = new Uint8Array([5, 10, 15, 15, 5, 20]); 
    
  // Calling length() function 
  b = A.length      
  c = B.length     
  d = C.length   
  e = D.length 
  f = E.length 
    
    
  // Printing the length of the typedArray 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d +"<br>"); 
  document.write(e +"<br>"); 
  document.write(f +"<br>"); 
    
</script> 
```

Output:

```
7
2
3
5
6
```

Code #2:

```
<script> 
  
  // Creating some ArrayBuffer with a size in bytes 
  const A = new ArrayBuffer(8); 
  const B = new ArrayBuffer(6); 
  const C = new ArrayBuffer(16); 
  const D = new ArrayBuffer(32); 
    
  // Creating some typedArray with the above sizes  
  // of the buffer 
  const E = new Uint8Array(A); 
  const F = new Uint8Array(B); 
  const G = new Uint8Array(C); 
  const H = new Uint8Array(D); 
    
  // Calling length property 
  a = E.length 
  b = F.length 
  c = G.length 
  d = H.length 
  
  // Printing the length of the typedArray 
  document.write(a +"<br>"); 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d); 
    
</script> 
```

Output:

```
8
6
16
32
```