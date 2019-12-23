---
title: JavaScript parseInt() with Examples
image: "/assets/default-social-image.png"
categories: JavaScript-functions
---

The parseInt() is a JavaScript built-in function that is used to recognize the string and transform it to an integer. It returns an integer of the given radix(base) that is acknowledged as the parseInt() function's second parameter. If there is no numeric value in the string, it returns  i.e., NaN, not a number.

**Syntax:**

`parseInt(Value, radix)`

Parameters: Two parameters specified below are accepted

value "Value" contains a string translated to an integer.
radix: This parameter is an optional and represents as radix or base to be used.

Return value: returns a number and the function returns NaN if the first character can not be converted to a number. It simply returns a number parsed up to that point where it finds a character that is not a number in the radix (base) mentioned.

Example:

```
Input: var n = parseInt("2018@geeksforgeeks");
Output: n = 2018
now n contains 2018 as '@' is not a Number 
and parsing stops at that point,further characters are ignored.
Input: var a = parseInt("1000");
Output: a = 1000(Number)
```

Code to show the working of parseInt() function:

**Code #1:**

```
<!DOCTYPE html> 
<html> 
<body> 
    <script> 
      
        a = parseInt("100"); 
        document.write('parseInt("100") = ' + a + "<br>"); 
          
        // It returns a Integer until 
        // it encounters Not a Number character 
        b = parseInt("2018@griva"); 
        document.write('parseInt("2018@griva") = ' + b + "<br>"); 
          
        // It returns NaN on Non numeral character 
        c = parseInt("griva@2018"); 
        document.write('parseInt("griva@2018") = ' + c + "<br>"); 
          
        // It returns Integer value of a Floating point Number 
        d = parseInt("3.14"); 
        document.write('parseInt("3.14") = ' + d + "<br>"); 
          
        // It returns only first Number it encounters 
        e = parseInt("21 7 2018"); 
        document.write('parseInt("21 7 2018") = ' + e + "<br>"); 
      
    </script> 
  
</body> 
</html> 
```

Output:

```
parseInt("100") = 100
parseInt("2018@griva") = 2018
parseInt("griva@2018") = NaN
parseInt("3.14") = 3
parseInt("21 7 2018") = 21
```

**Code #2:**

If the radix is not specified in the function parseInt() and the string start includes "0x" than the hexadecimal value is processed. The radix is 10 (decimal) by choice. Notice that there is '8' in line 11, which is a character not specified in the number system of radix 8, so it returns NaN.

```
<!DOCTYPE html> 
<html> 
    <body> 
        <script> 
          
        //base 10 
        a = parseInt("100",10); 
        document.write('parseInt("100",10) = ' + a + "<br>"); 
          
        //base 8 
        b = parseInt("8",8); 
        document.write('parseInt("8",8) = ' + b + "<br>"); 
          
        //base 8 
        c = parseInt("15",8); 
        document.write('parseInt("15",8) = ' + c + "<br>"); 
          
        //base 16 
        d = parseInt("16",16); 
        document.write('parseInt("16",16) = ' + d + "<br>"); 
          
        // Leading and trailing spaces are ignored in parseInt() function 
        e = parseInt(" 100 "); 
        document.write('parseInt(" 100 ") = ' + e + "<br>"); 
          
        //base 16(hexadecimal) 
        f = parseInt("0x16"); 
        document.write('parseInt("0x16") = ' + f + "<br>"); 
          
        </script> 
      
    </body> 
</html> 
```

Output:

```
parseInt("100",10) = 100
parseInt("8",8) = NaN
parseInt("15",8) = 13
parseInt("16",16) = 22
parseInt(" 100 ") = 100
parseInt("0x16") = 22
```