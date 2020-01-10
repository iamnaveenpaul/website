---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.byteOffset property
categories: JavaScript-typedArray
---

The typedArray.byteOffset is a built-in property in JavaScript that is used from the beginning of its ArrayBuffer to return the offset of bytes of a specified typedArray.

**Syntax:**

`typedArray.byteOffset`

**Parameter:**

It accepts no parameters because it is not a function, but a property.

**Return value:**

From the beginning of its ArrayBuffer, it returns the offset in bytes of a specified typedArray.

Example;

```
<script> 
  
    // Constructing some ArrayBuffers 
    var buffer1 = new ArrayBuffer(2); 
    var buffer2 = new ArrayBuffer(8); 
    var buffer3 = new ArrayBuffer(16); 
    var buffer4 = new ArrayBuffer(32); 
  
    // Constructing some typedArray with 
    // parameter of above buffers 
    var A = new Uint8Array(buffer1); 
    var B = new Uint8Array(buffer2, 4); 
    var C = new Uint8Array(buffer3, 5); 
    var D = new Uint8Array(buffer4, 8); 
  
   // Calling byteOffset property 
    a = A.byteOffset; 
    b = B.byteOffset; 
    c = C.byteOffset; 
    d = D.byteOffset; 
  
   // Printing the offset in bytes of 
   // the above typedArray from the start 
   // of its ArrayBuffer 
   document.write(a + "<br>"); 
   document.write(b + "<br>"); 
   document.write(c + "<br>"); 
   document.write(d); 
  
</script> 
```

Output:

```
0
4
5
8
```