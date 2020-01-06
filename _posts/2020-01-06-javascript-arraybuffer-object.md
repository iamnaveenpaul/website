---
image: "/assets/default-social-image.png"
title: JavaScript ArrayBuffer Object
categories: JavaScript-array
---

To represent a generic fixed-length raw binary data buffer, an ArrayBuffer object is used. An ArrayBuffer's contents can not be modified explicitly and can only be accessed via a DataView Object or one of the array objects that are typed. Such objects are used to read and write the buffer contents. One ArrayBuffer can be added to more than one DataView or typed array object and any changes to one object can be easily seen from the view of the other objects.

The typed arrays are:

Float32Array, Float64Array, Int8Array, Int16Array, Int32Array, Uint8Array, Uint8ClampedArray, Uint16Array, Uint32Array.

**Syntax:**

`new ArrayBuffer(byteLength)`

**Parameters:** It accepts one parameter, i.e. bytelength, specifying the size of the array buffer to be generated in bytes.

**Return value:** It returns the defined size of a new ArrayBuffer object and initializes the value to 0.

Example:

```
<script> 
  
    //Create a 16byte buffer 
    var buffer = new ArrayBuffer(16); 
  
    //Create a DataView referring to the buffer 
    var view1 = new DataView(buffer); 
  
    //Create a Int8Array view referring to the buffer 
    var view2 = new Int8Array(buffer); 
  
    //Put value of 32bits 
    view1.setInt32(0, 0x76543210); 
  
    //prints the 32bit value 
    document.write(view1.getInt32(0).toString(16) + "<br>");  
      
    //prints only 8bit value  
    document.write(view1.getInt8(0).toString(16) + "<br>");  
    document.write(view2[0].toString(16)); 
  
</script> 
```

Output:

```
76543210
76
76
```

**Properties :**

* ArrayBuffer.byteLength: byteLength returns the buffer length in bytes.
* ArrayBuffer.prototype: This attribute allows all ArrayBuffer objects to add properties.

**Methods:**

* ArrayBuffer.isView(arg): When arg is one of the views of ArrayBuffer (typed array objects or a DataView) then it returns true otherwise it returns false.
* ArrayBuffer.transfer(oldBuffer [,newByteLength]): the contents of the specified oldbuffer are either truncated or zero-extended by the specified newByteLength and returned as a new ArrayBuffer.

**Instance Methods:**

ArrayBuffer.slice() and ArrayBuffer.prototype.slice(): returns a new ArrayBuffer whose content is an exclusive copy of the bytes of this ArrayBuffer from the beginning, including, up to the end.