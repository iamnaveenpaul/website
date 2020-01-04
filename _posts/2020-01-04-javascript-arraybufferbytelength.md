---
title: JavaScript arrayBuffer.byteLength
image: "/assets/default-social-image.png"
categories: JavaScript-array
---

The arrayBuffer.byteLength is a JavaScript property that provides bytes for the length of an arrayBuffer.

**Syntax:**

`ArrayBuffer.byteLength`

**Parameters:** It does not allow any parameters to be accepted because arrayBuffer.byteLength is not a function but a property.
**Return Value:** This returns an arrayBuffer's length in bytes.

Code #1:

```
<script> 
  
    // Creation of arrayBuffer of size 5 bytes 
    var A = new ArrayBuffer(5); 
  
    // Using property byteLength 
    var bytes1 = A.byteLength; 
  
    // Printing the lengths of the ArrayBuffer 
    document.write(bytes1); 
  
</script> 
```

Output:

`5`

**Errors and Exception:**

If the arrayBuffer's length is given in a fraction, it returns the length in the whole number and if the length is given in the form of a string it returns the length of zero (0).

Code #1:

```
<script> 
  
    // Creation of arrayBuffer of sizes 5.6 
    var A = new ArrayBuffer(5.6); 
  
   // Using property byteLength 
   var bytes1 = A.byteLength; 
  
   // Printing the length of the ArrayBuffer 
   document.write(bytes1); 
  
</script> 
```

Output:

`5`

Code #2:

```
<script> 
  
    // Creation of arrayBuffers of sizes "a" bytes 
    var A = new ArrayBuffer("a"); 
  
    // Using property byteLength 
    var bytes1 = A.byteLength; 
  
    // Printing the length of the ArrayBuffer 
    document.write(bytes1); 
  
</script> 
```

Output:

`0`