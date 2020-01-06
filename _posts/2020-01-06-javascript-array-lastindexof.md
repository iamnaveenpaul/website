---
image: "/assets/default-social-image.png"
title: JavaScript Array lastIndexOf()
categories: JavaScript-array
---

The function arr.lastIndexOf() is used to find the index of the last search element that was provided as the function argument.

**Syntax:**

`arr.lastIndexOf(searchElement[,index])`

**Arguments:** The first argument for this method is the searchElement, the element in the array to be searched. Second argument to this function is the optional index argument that defines the starting index in the array from which to scan the element backwards. If this argument is not given, then index arr.length – is used to begin the backward search as the default value.

**Return value:** This function returns the index of the searchElement's last appearance. If you cannot locate the item in the array, this function returns -1

Example 1:

```
var array = [2, 9, 9];
print(array.lastIndexOf(2));
```

Output:

`0`

The lastIndexOf() function returns the last occurrence index of 2 which is 0

Example 2:

```
var array = [2, 98, 12, 45];
print(array.lastIndexOf(45,2));
```

Output:

`-1`

The lastIndexOf() function finds the last occurrence index of 45 in this instance. Therefore the function returns -1 as it is not present starting from index 2.

Example 3:

```
var array = [2, 98, 12, 45];
print(array.lastIndexOf(98,2));
```

Output:

`1`

The lastIndexOF() method returns the last 98 occurrence as 1.

Example 4:

```
var array = [2, 98, 12, 45];
print(array.lastIndexOf(100));
```

Output:

`-1`

The lastIndexOF() function tests the last 100 occurrence in this case. So, as it is not there, it returns -1

Example 5:

```
var array = [2, 98, 12, 98];
print(array.lastIndexOf(98));
```

Output:

`3`

Program 1:

```
<script> 
// JavaScript to illustrate lastIndexOf()  
  
function func() { 
  
    // Original array 
    var array = [2, 9, 9]; 
    document.write(array.lastIndexOf(2)); 
} 
  
func(); 
</script> 
```

Output:

`0`

Program 2:

```
<script> 
// JavaScript to illustrate lastIndexOf()  
  
function func() { 
  
    //Original array 
    var array = [2, 98, 12, 45]; 
    document.write(array.lastIndexOf(45,2)); 
} 
  
func(); 
</script> 
```

Output:

`-1`

Program 3:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
  
    // Original array 
    var array = [2, 98, 12, 45]; 
    document.write(array.lastIndexOf(98,2)); 
} 
  
func(); 
</script> 
```

Output:

`1`

Program 4:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
  
    // Original array 
    var array = [2, 98, 12, 45]; 
    document.write(array.lastIndexOf(100)); 
} 
func(); 
</script> 
```

Output:

`-1`

Program 5:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
  
    //Original array 
    var array = [2, 98, 12, 98]; 
    document.write(array.lastIndexOf(98)); 
} 
func(); 
</script> 
```

Output:

`3`