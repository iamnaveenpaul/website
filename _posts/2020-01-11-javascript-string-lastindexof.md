---
image: "/assets/default-social-image.png"
title: JavaScript String lastIndexOf()
categories: JavaScript-strings
---

The str.lastIndexOf() method locates the index of the last argument string instance in the specified array. The returned value is 0-based.

**Syntax:**

`str.lastIndexOf(searchValue , index)`

**Arguments**

The first argument to the searchValue method is the variable to be checked within the base string. The second argument to the function index determines the beginning index from which the searchValue in the base string is to be checked backwards.

**Return value**

This function returns the string index (0-based), where the last time the searchValue has been identified. When searchValue can't be found in the string, then the method returns -1.

Example 1:

```
var str = 'Departed Train';
var index = str.lastIndexOf('Train');
print(index); 
```

Output:

`9`

In this case the lastIndexOf() method would locate the last index of the 'Train' string in the string str. Because the string's only index is 9, this function returns 9 as the result.

Example 2:

```
var str = 'Departed Train';
var index = str.lastIndexOf('ed Tr');
print(index); 
```

Output:

`6`

The lastIndexOf() function seeks the last index in the array string of the string 'ed Tr' in this string str. Therefore this function returns 6 as the answer since the only index of where this string is present is 6.

Example 3:

`print('Departed Train'.lastIndexOf('train')); `

Output:

`6`

The lastIndexOf() function finds the last index of the string 'train' in the string str in this case. Therefore this function returns -1 as the result, as the string is not present in any index in str.

Example 4:

`print('Departed Train before another Train'.lastIndexOf('Train')); ; `

Output:

`6`

In this instance, the lastIndexOf() function will find the last string Train index in string str. Since the string is present in the string str and the index 30 twice, this function is Train's last index, so it returns 30 as the answer.

Program 1:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
      
    //Original string 
    var str = 'Departed Train'; 
      
    //Finding the index of the string 
    var index = str.lastIndexOf('Train'); 
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
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
      
    // Original string 
    var str = 'Departed Train'; 
      
    // Finding the index of the string 
    var index = str.lastIndexOf('ed Tr'); 
    document.write(index);  
} 
func(); 
</script>  
```

Output:

`6`

Program 3:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
     
    // Original string 
    var str = 'Departed Train'; 
      
    // Finding index of occurrence of 'train' 
    var index = str.lastIndexOf('train'); 
    document.write(index); 
} 
func(); 
</script> 
```

Output:

`-1`

Program 4:

```
<script> 
// JavaScript to illustrate lastIndexOf() function 
  
function func() { 
       
    // Original string 
    var str = 'Departed Train before another Train'; 
      
    // Finding index of occurrence of 'Train' 
    var index = str.lastIndexOf('Train'); 
    document.write(index); ; 
} 
func(); 
</script> 
```

Output:

`30`