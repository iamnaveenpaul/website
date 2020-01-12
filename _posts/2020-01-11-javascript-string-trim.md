---
image: "/assets/default-social-image.png"
title: JavaScript String trim()
categories: JavaScript-strings
---

**str.trim()**

str.trim() removes the white spaces from both ends of the given string.

**Syntax:**

`str.trim()`

**Arguments**

This function takes up no arguments at all.

**Return value**

This method returns a new string, without any of the White spaces preceding or trailing.

Example 1:

```
var str = "GrivaForCoding      ";
var st = str.trim();
print(st);
```

Output:

`GrivaForCoding`

The trim() function in this illustration eliminates all leading and trailing spaces in string str.

Example 2:

```
var str = "   GrivaForCoding";
var st = str.trim();
print(st);
```

Output:

`GrivaForCoding`

The trim() function in this illustration eliminates all leading and trailing spaces in string str.

Program 1:

```
<script> 
// JavaScript Program to illustrate trim() function 
  
function func() { 
  
    // Original string containing whitespace 
    var str = "GrivaForCoding      "; 
  
    // Trimmed string 
    var st = str.trim(); 
    document.write(st);  
} 
  
func(); 
</script> 
```

Output:

`GrivaForCoding`

Program 2:

```
<script> 
// JavaScript Program to illustrate trim() function 
  
function func() { 
  
    // Original string containing whitespace 
    var str = "   GrivaForCoding"; 
  
    // Trimmed string 
    var st = str.trim(); 
    document.write(st);   
} 
func(); 
</script> 
```

Output:

`GrivaForCoding`

**str.trimLeft()**

The str.trimLeft() function removes the white spaces from the beginning of the given string. The trailing white spaces are not impacted.

**Syntax:**

`str.trimLeft()`

**Arguments**

This function takes up no arguments at all.

**Return value**

This method returns a new string without any of the white spaces that are leading.

Example 1:

```
var str = "      GrivaForCoding      ";
var st = str.trimLeft();
print(st);
```

Output:

`GrivaForCoding`

The trimLeft() method eliminates all leading spaces in this case but the trailing spaces in the string str stay as they would be.

Example 2:

```
var str = "   GrivaForCoding";
var st = str.trim();
print(st);
```

Output:

`GrivaForCoding`

In this illustration the function trimLeft() extracts all lead spaces from str.

Program 1:

```
<script> 
// JavaScript Program to illustrate trimLeft() 
// funtion 
  
function func() { 
  
    // Original string containing whitespace 
    var str = "GrivaForCoding      "; 
  
    // Trimmed string 
    var st = str.trimLeft(); 
    document.write(st);   
} 
  
func(); 
</script> 
```

Output:

`GrivaForCoding       `

Program 2:

```
<script> 
// JavaScript Program to illustrate trimLeft() 
// function 
  
function func() { 
  
    // Original string containing whitespace 
    var str = "   GrivaForCoding"; 
  
    // Trimmed string 
    var st = str.trimLeft(); 
    document.write(st);   
} 
func(); 
</script> 
```

Output:

`GrivaForCoding`

**str.trimRight()**

str.trimRight() is for eliminating white spaces from the end of the string. At the beginning of the string, it does not impact the white spaces.

**Syntax:**

`str.trimRight()`

**Arguments**

There are no arguments for this function.

**Return value**

This method returns a new string, without any white spaces trailing off.

Example 1:

```
var str = "GrivaForCoding      ";
var st = str.trimRight();
print(st);
```

Output:

`GrivaForCoding`

In this case, the function trimRight() eliminates all trailing spaces from the string str.

Example 2:

```
var str = "   GrivaForCoding";
var st = str.trimRight();
print(st);
```

Output:

`     GrivaForCoding`

In this case, the function trimRight() doesn't eliminates all trailing spaces from the string str.

Program 1:

```
// JavaScript Program to illustrate trimRight() 
// function 
<script> 
function func() { 
  
    // Original string containing whitespace 
    var str = "GrivaForCoding      "; 
  
    // Trimmed string 
    var st = str.trimRight(); 
    document.write(st);   
} 
func(); 
</script> 
```

Output:

`GrivaForCoding       `

Program 2:

```
<script> 
// JavaScript Program to illustrate trimRight()  
// funtion 
  
function func() { 
  
    // Original string containing whitespace 
    var str = "   GrivaForCoding"; 
  
    // Trimmed string 
    var st = str.trimRight(); 
    document.write(st);   
} 
  
func(); 
</script> 
```

Output:

`     GrivaForCoding`