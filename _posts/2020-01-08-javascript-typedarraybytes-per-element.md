---
title: JavaScript typedArray.BYTES_PER_ELEMENT
image: "/assets/default-social-image.png"
categories: JavaScript-typedArray
---

The typedArray.BYTES_PER_ELEMENT is a built-in property in JavaScript that is used in a given typedArray to return the size in bytes of each element.

**Syntax:**

`typedArray.BYTES_PER_ELEMENT;`

**Parameter:**

It acknowledges no parameters because it is not a function but a property.

**Return value:**

It returns each element's size in bytes in a given tyepedArray.

Example:

```
<script> 
  
    // Calling BYTES_PER_ELEMENT on some typedArray 
    a = Int8Array.BYTES_PER_ELEMENT; 
    b = Uint8Array.BYTES_PER_ELEMENT; 
    c = Uint8ClampedArray.BYTES_PER_ELEMENT; 
    d = Int16Array.BYTES_PER_ELEMENT; 
    e = Uint16Array.BYTES_PER_ELEMENT; 
    f = Int32Array.BYTES_PER_ELEMENT; 
    g = Uint32Array.BYTES_PER_ELEMENT; 
    h = Float32Array.BYTES_PER_ELEMENT; 
    i = Float64Array.BYTES_PER_ELEMENT; 
  
   // Printing the size in bytes of the 
   // each element in the given typedArray. 
   document.write(a + "<br>"); 
   document.write(b + "<br>"); 
   document.write(c + "<br>"); 
   document.write(d + "<br>"); 
   document.write(e + "<br>"); 
   document.write(f + "<br>"); 
   document.write(g + "<br>"); 
   document.write(h + "<br>"); 
   document.write(i); 
  
</script> 
```

Output:

```
1
1
1
2
2
4
4
4
8
```