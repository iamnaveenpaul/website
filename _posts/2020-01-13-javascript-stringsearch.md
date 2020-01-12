---
title: JavaScript string.search()
image: "/assets/default-social-image.png"
categories: JavaScript-strings
---

The string.search() function is the JavaScript built-in method used to search for a match in standard contexts and provided string object.

**Syntax:**

`string.search( A )`

**Parameters:**

This approach takes a single parameter A that represents the object in regular expression.

**Return Value:**

The first match string index between the regular expression and the given string object is returned by this function and returns-1, if no match is found. Indexing starts at zero (0), but the alphabet matches at first, then the index of the first matched alphabet will not check again. It simply returns it.

Example 1:

```
<script> 
  
// Taking input a string. 
var string = "GrivaforCoding"; 
  
// Taking a regular expression. 
var re1 = /G/; 
var re2 = /e/; 
var re3 = /s/; 
  
// Printing the index of matching alphabets 
document.write(string.search(re1) + "<br>"); 
document.write(string.search(re2) + "<br>"); 
document.write(string.search(re3)); 
  
< /script> 
```

Output:

```
0
1
4
```

Example 2:

This example gives -1 as there is no match between a regular and the input string expression

```
<script> 
  
// Taking input a string. 
var string = "GrivaforCoding"; 
  
// Taking a regular expression. 
var re1 = /p/; 
var re2 = /1/; 
var re3 = / /; 
var re4 = /, /; 
  
// Printing the index of matching alphabets 
document.write(string.search(re1) + "<br>"); 
document.write(string.search(re2) + "<br>"); 
document.write(string.search(re3) + "<br>"); 
document.write(string.search(re4)); 
  
< /script> 
```

Output:

```
-1
-1
-1
-1
```