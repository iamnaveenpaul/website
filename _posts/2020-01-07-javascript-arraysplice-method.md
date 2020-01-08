---
image: "/assets/default-social-image.png"
title: JavaScript Array.splice() Method
categories: JavaScript-array
---

The Array.splice() method is an built-in method in JavaScript that is used by removing existing elements and/or adding new elements to modify the contents of an array.

**Syntax:**

`Array.splice( index, remove_count, item_list )`

**Parameter:**

This method recognizes many of the parameters listed below:

* **index:** It is a parameter that is required. This is the index that begins to modify the array (with origin at 0). This can also be negative which starts after the counting such of many elements from the end.
* **remove_count:** The number of elements from the start index to be removed.
* **items_list:** The list of new items to be inserted from the starting index separated by comma operator.

**Return Value:**

While it mutates in place the original array, it still returns the list of arrays that have been removed. If no array is removed, it returns an empty array.

Example:

```
<script> 
var languages = ['C++', 'Java', 'Html', 'Python', 'C']; 
  
document.write(languages + "<br>"); 
  
// Add 'Julia' and 'Php' after removing 'Html'. 
var removed = languages.splice(2, 1, 'Julia', 'Php') 
  
document.write(languages + "<br>"); 
document.write(removed + "<br>"); 
  
// No Removing only Insertion from 2nd index from the ending 
languages.splice(-2, 0, 'Pascal') 
document.write(languages) 
</script> 
```

Output:

```
C++,Java,Html,Python,C
C++,Java,Julia,Php,Python,C
Html
C++,Java,Julia,Php,Pascal,Python,C
```