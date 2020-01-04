---
image: "/assets/default-social-image.png"
title: JavaScript Array.isArray()
categories: JavaScript-array
---

The feature Array.isArray() specifies whether or not the value passed is an array. If the passed argument is array, this method returns true else it returns false.

**Syntax**

`Array.isArray(obj)`

**Argument**

Here object in JavaScript is any valid object such as map, list, array, string, etc.

**Return value**

This method returns the value of Boolean true if the passed argument is array otherwise it returns false

Example 1:

```
Input:
print(Array.isArray(['Day','Night','Evening']));

Output:
true
```

Therefore this function returns true as the answer because the argument passed to the function isArray() is an array.

Example 2:

```
Input:
print(Array.isArray({foo: 123}));

Output:
false
```

Therefore this function returns false as the answer because the argument passed to the function isArray() is a map.

Example 3:

```
Input:
print(Array.isArray('foobar'));

Output:
false
```

Therefore this function returns false as the answer because the argument passed to the function isArray() is a string.

Program 1:

```
<script> 
// JavaScript code for isArray() function 
function func() { 
    document.write(Array.isArray(['Day','Night','Evening'])); 
} 
  
func(); 
</script> 
```

Output:

`true`

Program 2:

```
<script> 
// JavaScript code for isArray() function 
function func() { 
    document.write(Array.isArray({foo: 123})); 
} 
  
func(); 
</script> 
```

Output:

`false`

Program 3:

```
<script> 
// JavaScript code for isArray() function 
function func() { 
    document.write(Array.isArray('foobar')); 
} 
  
func(); 
</script> 
```

Output:

`false`