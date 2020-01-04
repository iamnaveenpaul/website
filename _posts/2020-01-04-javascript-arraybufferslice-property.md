---
image: "/assets/default-social-image.png"
title: JavaScript arrayBuffer.slice() property
categories: JavaScript-array
---

The arrayBuffer.slice is a JavaScript property that returns the other arrayBuffer that includes the contents of the previous arrayBuffer from start to finish, purely in bytes. ArrayBuffer is an object that represents binary data of fixed length.

**Difference between property and function in javascript.**

Property is nothing but a value in JavaScript, while method is a function.

**Syntax:**

`arraybuffer.slice(begin[, end])`

**Parameters Used:**

**begin :** The slicing starts from the byte index that is zero based.
**end :** At this index byte the slicing stops. If the end is found unspecified, the new ArrayBuffer will contain all the contents. The current array must have a valid index range. If the current length of the ArrayBuffer is found to be negative, it is set to zero.

**Return Value:**

The property returns an object, new ArrayBuffer.

Examples:

```
Input : uint32View[1] = 31
        myBuffer.slice(4, 12)
        sliced_bu[0]
Output : 31

Input : uint32View[1] = 32
        myBuffer.slice(4, 12)
        sliced_bu[0]
Output : 32
```

```
<script> 
// create an ArrayBuffer with a size 25 in bytes 
var myBuffer = new ArrayBuffer(16); 
  
// produces Uint32Array [0, 0, 0, 0] 
var uint32View = new Uint32Array(myBuffer); 
  
uint32View[1] = 30; 
  
// produces Uint32Array [30, 0] 
var sliced_buf = new Uint32Array(myBuffer.slice(4, 12)); 
  
// expected output: 30 
console.log(sliced_buf[0]); 
< /script> 
```

Output:

`30`