---
image: "/assets/default-social-image.png"
title: JavaScript Array reverse()
categories: JavaScript-array
---

arr.reverse() is used to reverse the array in place. The array's first element is the last element and vice versa.

**Syntax:**

`arr.reverse()`

**Argument**

There is no argument for this function.

**Return value**

This feature returns the original array reversed reference.

Example 1:

```
var arr = [34, 234, 567, 4];
print(arr);
var new_arr = arr.reverse();
print(new_arr);
```

Output:

```
34, 234, 567, 4
4, 567, 234, 34
```

In this example, the reverse() function reverses the arr array element sequence.

Program 1:

```
<script> 
// JavaScript to illustrate reverse() function 
  
function func() { 
  
    //Original Array 
    var arr = [34, 234, 567, 4]; 
    document.write(arr); 
  
    //Reversed array 
    var new_arr = arr.reverse(); 
    document.write("<br>"); 
    document.write(new_arr); 
} 
func(); 
</script> 
```

Output:

```
34, 234, 567, 4
4, 567, 234, 34
```