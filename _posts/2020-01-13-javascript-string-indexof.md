---
image: "/assets/default-social-image.png"
title: JavaScript String indexOf()
cateories: JavaScript-strings
---

The str.indexOf() function locates the index of the first argument string instance in the specified array. The returned value is 0-based.

**Syntax:**

`str.indexOf(searchValue , index)`

**Arguments**

The first argument to the searchValue method is a string to be scanned in the base string. The second argument to the function index specifies the starting index from which to search the searchValue in the base string.

**Return value**

This function returns the string index (0-based) in which the searchValue was first found. If it cannot find the searchValue in the string then the function returns -1.

Example 1:

`print('Departed Train'.indexOf('Train')); `

In this case the indexOf() method must find the string Train index. Therefore this function returns 9 as the response since the first and only series where this string is present is 9.

Output:

`9`

Example 2:

`print('Departed Train'.indexOf('ed Tr')); `

Output:

`6`

In this case. the indexOf() method must consider the string index ed Tr. Therefore this function returns 6 as the answer since the first and only index where this string is present is 6.

Example 3:

`print('Departed Train'.indexOf('train')); `

Output:

`-1`

In this case, the indexOf() method must find the string Train index. Therefore this function returns -1 as the response, since the searchValue is not present in the string.

Example 4:

`print('Departed Train before another Train'.indexOf('Train')); `

Output:

`9`

In this example the indexOf() function will find the string Train index. Therefore this function returns 9 as the response since the first index of the searchValue is 9.

Program 1:

```
// JavaScript to illustrate indexOf() function 
<script> 
function func() { 
  
    // Original string 
    var str = 'Departed Train'; 
  
    // Finding index of occurrence of 'Train' 
    var index = str.indexOf('Train'); 
    document.write(index);  
} 
func(); 
</script> 
```

Output:

`9`

Program 2:

```
<script> 
// JavaScript to illustrate indexOf() function 
function func() { 
  
    // Original string 
    var str = 'Departed Train'; 
  
    // Finding index of occurrence of 'Train' 
    var index = str.indexOf('ed Tr'); 
    document.write(index);   
} 
func(); 
</script> 
```

Output:

`6`

Program 3:

```
// JavaScript to illustrate indexOf() function 
<script> 
function func() { 
  
    // Original string 
    var str = 'Departed Train'; 
  
    // Finding index of occurrence of 'Train' 
    var index = str.indexOf('train'); 
    document.write(index);   
} 
func(); 
</script> 
```

Output:

`-1`

Program 4:

```
// JavaScript to illustrate indexOf() function 
<script> 
function func() { 
  
    // Original string 
    var str = 'Departed Train before another Train'; 
  
    // Finding index of occurrence of 'Train' 
    var index = str.indexOf('Train'); 
    document.write(index);   
} 
func(); 
</script> 
```

Output:

`9`