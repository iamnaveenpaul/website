---
image: "/assets/default-social-image.png"
title: JavaScript ArrayBuffer.isView()
categories: JavaScript-array
---

The ArrayBuffer.isView() is a JavaScript built-in function that is used to check whether or not the given function argument is typed array.

**List of typed array:**

```
Int8Array();
Uint8Array();
Uint8ClampedArray();
Int16Array();
Uint16Array();
Int32Array();
Uint32Array();
Float32Array();
Float64Array();
```

**Syntax:**

`ArrayBuffer.isView(p)`

**Parameters:** It accepts a parameter in the form of either a typed array or something else.
**Return Values:** If the parameter is typed array, it returns true otherwise it returns false.

Code #1:

```
<script> 
  
  // Creation of ArrayBuffer having a size in bytes 
  var buffer = new ArrayBuffer(12); 
  
  // Use of ArrayBuffer.isView function 
  A = ArrayBuffer.isView(new Int32Array()) 
  document.write(A); 
  
</script> 
```

Output:

`true`

Note: The output here is true because Int32Array is an array that is typed.

Code #2:

```
<script> 
  
  // Creation of ArrayBuffer having size in bytes 
  var buffer = new ArrayBuffer(12); 
  
  // Use of ArrayBuffer.isView function 
  A = ArrayBuffer.isView(); 
  B = ArrayBuffer.isView(null); 
  C = ArrayBuffer.isView(undefined); 
  
  // Printing the result 
  document.write(A + '<br>'); 
  document.write(B + '<br>'); 
  document.write(C + '<br>'); 

</script> 
```

Output:

```
false
false
false
```

Note: The output here is false because the arguments above are not typed array.