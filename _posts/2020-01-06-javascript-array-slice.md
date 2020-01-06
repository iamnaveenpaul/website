---
image: "/assets/default-social-image.png"
title: JavaScript Array slice()
categories: JavaScript-array
---

The method arr.slice() returns a new array that includes a component of the array to be enforced. The original stays the same.

**Syntax**

`arr.slice(begin, end)`

**Arguments**

There are two optional arguments for this function. The first argument defines where the portion is to be extracted from the starting index. If this argument is absent, the function must start as 0 because it is the default start value. The function's second argument is the index to which the portion (excluding the end index) is to be extracted. If this argument is not specified, the array will be extracted until the end as it is the default end value if the end value is larger than the array length, then the end value will alter the array length.

**Return value**

This function returns a new array that contains part of the original array.

Example 1:

```
var arr = [23,56,87,32,75,13];
var new_arr = arr.slice();
print(arr);
print(new_arr);
```

Output:

```
[23,56,87,32,75,13]
[23,56,87,32,75,13]
```

In this case, the slice() function extracts the whole array from the specified string and returns it as the answer as no arguments have been passed to it.

Example 2:

```
var arr = [23,56,87,32,75,13];
var new_arr = arr.slice(2);
print(arr);
print(new_arr);
```

Output:

```
[23,56,87,32,75,13]
[87,32,75,13]
```

The slice() method extracts the array from index 2 to the end of the array in this example and returns it as the response.

Example 3:

```
var arr = [23,56,87,32,75,13];
var new_arr = arr.slice(2,4);
print(arr);
print(new_arr);
```

Output:

```
[23,56,87,32,75,13]
[87,32]
```

In this case, the slice() function extracts the array from the specified array beginning with index 2 and including all the elements below index 4.

Example 4:

```
var arr = [23,56,87,32,75,13];
var new_arr = arr.slice(3,10);
print(arr);
print(new_arr);
```

Output:

```
[23,56,87,32,75,13]
[32,75,13]
```

In this case, the slice() method extracts the array from the index 3 to the end of the array because the specified upper limit is greater than the array size.

Program 1:

```
//JavaScript to illustrate slice() function 
<script> 
function func() { 
  
    //Original Array 
    var arr = [23,56,87,32,75,13]; 
  
    //Extracted array 
    var new_arr = arr.slice(); 
    document.write(arr); 
    document.write("<br>"); 
    document.write(new_arr); 
} 
func(); 
</script> 
```

Output:

```
[23,56,87,32,75,13]
[23,56,87,32,75,13]
```

Program 2:

```
//JavaScript to illustrate slice() function 
<script> 
function func() { 
  
    //Original Array 
    var arr = [23,56,87,32,75,13]; 
  
    //Extracted array 
    var new_arr = arr.slice(2); 
    document.write(arr); 
    document.write("<br>"); 
    document.write(new_arr);  
} 
func(); 
</script> 
```

Output:

```
[23,56,87,32,75,13]
[87,32,75,13]
```

Program 3:

```
//JavaScript to illustrate slice() function 
<script> 
function func() { 
  
    //Original Array 
    var arr = [23,56,87,32,75,13]; 
  
    //Extracted array 
    var new_arr = arr.slice(2,4); 
    document.write(arr); 
    document.write("<br>"); 
    document.write(new_arr); 
} 
func(); 
</script> 
```

Output:

```
[23,56,87,32,75,13]
[87,32]
```