---
image: "/assets/default-social-image.png"
title: JavaScript parseFloat() with Examples
categories: JavaScript-functions
---

The parseFloat() is a JavaScript built-in feature that is used to recognize the string and transform it to a floating point integer. If the string does not have a number attribute, or if the string's first character is not a number, then NaN is returned, i.e, not a number. This simply returns a floating point integer that has been parsed up to the point where it finds a character that is not a number.

**Syntax:**

`parseFloat(Value)`

Parameters: it takes a "value" parameter comprising a string that is translated to a number of floating point type.

Return value: returns a floating point number and if a string's first character can not be transformed to a number then NaN, i.e. not a number, is returned.

Example:

```
Input: var n = parseFloat("  2018  ");
Output: n=2018 (floating point Number)
The parseFloat() function ignores leading and trailing spaces and
returns the floating point Number of the string.

Input: var a = parseFloat("1000.04");
Output: now a = 1000.04(floating point Number)
```

Codes to show the working of this function:

**Code #1:**

```
<!DOCTYPE html> 
<html> 
  
<body> 
   <script> 
      // It ignores leading and trailing spaces. 
      a = parseFloat("  100  ") 
      document.write('parseFloat("  100  ") = ' +a +"<br>"); 
  
      // It returns floating point Number until 
      // it encounters Not a Number character 
      b = parseFloat("2018@geeksforgeeks") 
      document.write('parseFloat("2018@griva") = '+b +"<br>"); 
  
      // It returns NaN on Non numeral character 
      c = parseFloat("griva@2018") 
      document.write('parseFloat("griva@2018") = ' +c +"<br>"); 
  
      d = parseFloat("3.14") 
      document.write('parseFloat("3.14") = '+d +"<br>"); 
  
      // It returns only first Number it encounters 
      e = parseFloat("22 7 2018") 
      document.write('parseFloat("22 7 2018") = ' +e +"<br>"); 
        
    </script> 
  
</body> 
</html> 
```

Output:

```
parseFloat(" 100 ") = 100
parseFloat("2018@griva") = 2018
parseFloat("griva@2018") = NaN
parseFloat("3.14") = 3.14
parseFloat("22 7 2018") = 22
```

**Code #2:**

Using isNaN() to check whether or not converted values are valid numbers.

```
<!DOCTYPE html> 
<html> 
  
<body> 
   <script> 
      var x = parseFloat("3.14"); 
      if (isNaN(x)) 
          document.write("x is not a number" + "<br>"); 
      else
          document.write("x is a number" + "<br>"); 
  
      var y = parseFloat("griva"); 
      if (isNaN(y)) 
          document.write("y is not a number" + "<br>"); 
      else
          document.write("y is a number" + "<br>"); 
  
     // Difference between parseInt() and parseFloat() 
     var v1 = parseInt("3.14"); 
     var v2 = parseFloat("3.14"); 
  
     document.write('Using parseInt("3.14") = ' + v1 + "<br>"); 
     document.write('Using parseFloat("3.14") = ' + v2 + "<br>"); 
   </script> 
  
</body> 
</html> 
```

Output:

```
x is a number
y is not a number
Using parseInt("3.14") = 3
Using parseFloat("3.14") = 3.14
```