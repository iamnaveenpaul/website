---
image: "/assets/default-social-image.png"
title: JavaScript typedArray.buffer() and typedArray.byteLength()
categories: JavaScript-typedArray
---

The typedArray.buffer() is a JavaScript property that represents the ArrayBuffer referenced by a typedArray and the Array.byteLength() property represents the typedArray length in bytes.

Syntax:

```
typedArray.buffer
typedarray.byteLength
```

**Parameters:**

It accepts no parameter because it is not a function but a property.

**Return values: **

It will not return any value.

Code #1:

```
<script> 
  
    // creating some ArrayBuffers with a size in bytes 
    const buffer1 = new ArrayBuffer(8); 
    const buffer2 = new ArrayBuffer(12); 
    const buffer3 = new ArrayBuffer(20); 
    const buffer4 = new ArrayBuffer(22); 
    const buffer5 = new ArrayBuffer(4); 
  
    // Creating typedArray object for above buffers 
    const A = new Uint16Array(buffer1); 
    const B = new Uint16Array(buffer2); 
    const C = new Uint16Array(buffer3); 
    const D = new Uint16Array(buffer4); 
    const E = new Uint16Array(buffer5); 
  
    // Getting the length of the arrayBuffer 
    document.write(A.byteLength +"<br>"); 
    document.write(B.byteLength +"<br>"); 
    document.write(C.byteLength +"<br>"); 
    document.write(D.byteLength +"<br>"); 
    document.write(E.byteLength); 
      
</script> 
```

Output:

```
8
12
20
22
4
```