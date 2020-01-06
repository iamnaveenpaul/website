---
image: "/assets/default-social-image.png"
title: JavaScript Array indexOf()
categories: JavaScript-array
---

The function arr.indexOf() is used to find the index of the search element's first occurrence as the argument for the function.

**Syntax**

`arr.indexOf(searchElement[,index])`

**Arguments**

The first argument for this function is the searchElement, the element in the array to be scanned. The second argument for this function is the optional index argument that specifies the starting index in the array from which to check the element. If this argument is not given then index 0 is used to start the search as the default value.

**Return value**

This function returns the index of the searchElement's first occurrence. If you can not locate the element in the array, this function returns-1

Example 1: The index of the first occurrence of 2 is found in the array in this illustration by the function indexOf(). However, as 2 is in place 0, it returns it as the response.

```
var array = [2, 9, 9];
print(array.indexOf(2));
```

Output:

`0`

Example 2: In this case, the indexOf() function searches in the array for 45 from index 2. Therefore, since it is located in place 3, it returns it as the response.

`var array = [2, 98, 12, 45];`

```
// Here second argument is starting index
// from where we need to search.
print(array.indexOf(45, 2));
```

Output:

`3`

Example 3: In this case, the indexOf() function checks 98 in the array from index 2. However, because it is not located, it returns-1 as the result.

```
var array = [2, 98, 12, 45];
print(array.indexOf(98,2));
```

Output:

`-1`

Example 4: In this case, the indexOf() function checks in the array for 100. However, as it is not identified, it returns-1 as the result.

```
var array = [2, 98, 12, 45];
print(array.indexOf(100));
```

Output:

`-1`

Example 5: In this example, the indexOf() function checks in the array for 98. However, since it is located in position 1, it returns 1 as the result.

```
var array = [2, 98, 12, 98];
print(array.indexOf(98));
```

Output:

`1`

Program 1:

```
// JavaScript to illustrate indexOf() function 
<script> 
function func() { 
    var array = [2, 9, 9]; 
    document.write(array.indexOf(2)); 
} 
func(); 
</script> 
```

Output:

`0`

Program 2:

```
// JavaScript to illustrate indexOf() function 
// with two parameters.  
<script> 
function func() { 
    var array = [2, 98, 12, 45]; 
  
    // Here second argument is starting index 
    // from where we need to search. 
    document.write(array.indexOf(45, 2)); 
} 
func(); 
</script> 
```

Output:

`3`

Program 3:

```
//JavaScript to illustrate indexOf() function 
<script> 
function func() { 
    var array = [2, 98, 12, 45]; 
    document.write(array.indexOf(98,2)); 
} 
func(); 
</script> 
```

Output:

`-1`

Program 4:

```
//JavaScript to illustrate indexOf() function 
<script> 
function func() { 
    var array = [2, 98, 12, 45]; 
    document.write(array.indexOf(100)); 
} 
func(); 
</script> 
```

Output:

`-1`

Program 5:

```
//JavaScript to illustrate indexOf() function 
<script> 
function func() { 
    var array = [2, 98, 12, 98]; 
    document.write(array.indexOf(98)); 
} 
func(); 
</script> 
```

Output:

`1`