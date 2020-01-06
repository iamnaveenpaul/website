---
image: "/assets/default-social-image.png"
title: JavaScript Array sort()
categories: JavaScript-array
---

arr.sort() method is used by the compare() function to sort the array in place in a given order. If the function is excluded, the ascending order of the array will be sorted.

**Syntax:**

`arr.sort([compareFunction])`

**Arguments**

The only argument for this method is a comparative function used to sort the elements of different attributes and order.

`compareFunction(a,b) < 0`

Then in the answer follows a before b.

`compareFunction(a,b) > 0`

Then in the answer follows b before a.

`compareFunction(a,b) = 0`

Then there is no shift in the order of a and b.

**Return value**

This function returns the initial array reference.

Example 1:

```
var arr = [2, 5, 8, 1, 4]
print(arr.sort());
print(arr);
```

Output:

```
1,2,4,5,8
1,2,4,5,8
```

The function sort() arranges the array elements in ascending order in this case.

Example 2:

```
var arr = [2, 5, 8, 1, 4]
print(arr.sort(function(a, b) {
  return a + 2 * b;
}));
print(arr);
```

Output:

```
2,5,8,1,4
2,5,8,1,4
```

The function sort() of the array elements is sorted according to the function assigned to each element in this case.

Program 1:

```
<script> 
// JavaScript to illustrate sort() function 
  
function func() { 
  
    //Original string 
    var arr = [2, 5, 8, 1, 4] 
  
    //Sorting the array 
    document.write(arr.sort()); 
    document.write("<br>"); 
    document.write(arr); 
} 
func(); 
</script> 
```

Output:

```
1,2,4,5,8
1,2,4,5,8
```

Program 2:

```
<script> 
// JavaScript to illustrate sort() function 
  
function func() { 
  
    // Original array 
    var arr = [2, 5, 8, 1, 4]; 
  
    document.write(arr.sort(function(a, b) { 
    return a + 2 * b; 
})); 
document.write("<br>"); 
document.write(arr); 
} 
func(); 
</script> 
```

Output:

```
4,1,8,5,2
4,1,8,5,2
```