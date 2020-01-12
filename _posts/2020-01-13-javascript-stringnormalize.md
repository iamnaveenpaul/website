---
image: "/assets/default-social-image.png"
title: JavaScript string.normalize()
categories: JavaScript-strings
---

The string.normalize() is a built-in function in javascript that is used to return a normalization Unicode representation of a specified input string. If the given input is not a string, it will be converted to string at first then this function will work.

**Syntax:**

`string.normalize([form])`

**Parameters:**

The parameter here is one of many types. These all state the Type of Unicode Normalization.:

* NFC: Normalization Form Canonical Composition.
* NFD: Normalization Form Canonical Decomposition.
* NFKC: Normalization Form Compatibility Composition.
* NFKD: Normalization Form Compatibility Decomposition.

**Return value:**

Returns a new string that includes the Unicode Normalization Type of the specified input string.

Example:

```
<script> 
  
  // Taking a string as input. 
  var a = "GrivaForCoding"; 
    
  // calling normalize function. 
  b = a.normalize('NFC') 
  c = a.normalize('NFD') 
  d = a.normalize('NFKC') 
  e = a.normalize('NFKD') 
    
  // Printing normalised form. 
  document.write(b +"<br>"); 
  document.write(c +"<br>"); 
  document.write(d +"<br>"); 
  document.write(e); 
    
</script> 
```

Output:

```
GrivaForCoding
GrivaForCoding
GrivaForCoding
GrivaForCoding
```

Reference:
[http://devdocs.io/javascript/global_objects/string/normalize](http://devdocs.io/javascript/global_objects/string/normalize)