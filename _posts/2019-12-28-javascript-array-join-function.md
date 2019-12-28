---
image: "/assets/default-social-image.png"
title: JavaScript Array join() function
categories: JavaScript-array
---

The function Array.join() is used to join the array elements into a string.

**Syntax:**

`Array.join([separator])`

**Argument: (separator)**

A string to distinguish the array's individual elements. You can leave it separated by comma (,) to default array element.

**Return Value:**

This function returns a string created by attaching the separator to all the elements of the array. If the separator is not provided, the elements of the array will be joined using comma(,) as this function is the default separator. If an empty string is provided as a separator then the elements are directly attached between them without any character.

Example 1:

```
var a = [1, 2, 3, 4, 5, 6];
print(a.join('|'));
```

Output:

`1|2|3|4|5|6`

In this case, the join() function binds the array elements to a string using '|'.

Example 2:

```
var a = [1, 2, 3, 4, 5, 6];
print(a.join()); 
```

Output:

`1, 2, 3, 4, 5, 6`

In this case, the join() method binds the array elements to a string using comma as it is the default value.

Example 3:

```
var a = [1, 2, 3, 4, 5, 6];
print(a.join(''));
```

Output:

`123456`

In this case, the join() method binds the array elements to a string using ' ' (empty string).

Program 1:

```
// JavaScript code for join() function 
<script> 
function func() { 
  var a = [ 1, 2, 3, 4, 5, 6 ]; 
  document.write(a.join('|')); 
} 
  
func(); 
< /script> 
```

Output:

`1|2|3|4|5|6`

Program 2:

```
// JavaScript code for join() function 
<script> 
function func() { 
  var a = [ 1, 2, 3, 4, 5, 6 ]; 
  document.write(a.join()); 
}  
  
func(); 
< /script> 
```

Output:

`1, 2, 3, 4, 5, 6`

Program 3:

```
// JavaScript code for join() function 
<script> 
function func() { 
  var a = [ 1, 2, 3, 4, 5, 6 ]; 
  document.write(a.join('')); 
} 
  
func(); 
< /script> 
```

Output:

`123456`