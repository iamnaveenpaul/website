---
image: "/assets/default-social-image.png"
title: JavaScript Operators
categories: JavaScript-operators
---

An operator is capable of manipulating a certain value or operand. Operators are used to perform specific mathematical and logical computations on operands. In other words, we can say that an operator operates the operands. In JavaScript operators are used for compare values, perform arithmetic operations etc. There are various operators supported by JavaScript:

* Arithmetic Operators
* Comparison Operators
* Logical Operators
* Assignment Operators
* Ternary Operators
* typeof Operator

**Arithmetic Operators:**

**+ (Addition) :**

‘+’ operator performs addition on two operands.

Example :

`Y = 5 + 5 gives Y = 10`
Note : ‘+’ operator can also be used to concatenate (add) strings.

Example :

`Y = "Geeks" + "for" + "Geeks" gives Y = "GeeksforGeeks"`

Example :

Y = "Geeks" + 4 + "Geeks" gives Y = "Geeks4Geeks"

**– (Subtraction) :**

‘-‘ operator performs subtraction on two operands.

Example :

`Y = 5 - 3 gives Y = 2 `

**`*` (Multiplication) :**

`*` operator performs multiplication on two operands.

Example :

`Y = 5 * 5 gives Y = 25`

**/ (Division) :**

‘/’ operator performs division on two operands (divide the numerator by the denominator).

Example :

`Y = 5 / 5 gives Y = 1`

**% (Modulus) :**

‘%’ operator gives remainder of an integer division.

Example :

```
A % B means remainder (A/B)
     Y = 5 % 4 gives Y = 1
```

**+ + (Increment) :**

‘+ +’ operator increases an integer value by one.

Example :

```
let A = 10 and Y = A + + then A = 11, Y=10
 if  A = 10 and Y = + + A then A = 11, Y=11
```

**– – (Decrement) :**

‘- -‘ operator decreases an integer value by one.

Example :

```
let A = 10 and Y = A - - then A = 9, Y=10
 if  A = 10 and Y = - - A then A = 9, Y=9
```

**Assignment Operators :**

**= (Assignment Operator) :**

Assigns right operand value to left operand.

Example :

`If A = 10 and Y = A then Y = 10`
             
**+= (Add and Assignment Operator) :**

Sums up left and right operand values and then assign the result to the left operand.

Example :

`Y += 1 gives Y = Y + 1 `

**– = (Subtract and Assignment Operator) :**

It subtract right side value from left side value and then assign the result to the left operand.

Example :

`Y -= 1 gives Y = Y - 1 `

similarly there are `*`= (Multiply and Assignment), /= (Divide and Assignment), %= (Modules and Assignment)

Example :

```
Y *= A is equivalent to Y = Y * A
Y /= A is equivalent to Y = Y / A
Y %= A is equivalent to Y = Y % A
```

**Comparison Operators :**

**= = :**

Compares the equality of two operands. If equal then the condition is true otherwise false.

Example :

```
Y = 5 and X = 6
  Y = = X is false.
```
             
Note : Type not considered in ‘= =’ operator.

**= = = :**

this operator compares equality of two operands with type.If equal(type and value both) then condition is true otherwise false.

Example :

```
given X = 10 then X = = = "10" is false.
X = = = 10 is true.
```
 
**!= (Not Equal) :**

Compares inequality of two operands. True if operands are not equal.

Example :

`given X = 10 then X ! = 11 is true. `

**> (Greater than) :**

this operator checks whether the left side value is greater than the right side value. If yes then it returns true otherwise it returns false.

Example :

`given X = 10 then X > 11 is false. `

**< (Less than) :**

this operator checks whether the left side value is less than right side value. If yes then it returns true otherwise it returns false.

Example :

`given X = 10 then X < 11 is true. `

**> = (Greater than or Equal to) :**

this operator checks whether the left side operand is greater than or equal to the right side operand. If yes then it returns true otherwise it returns false.

Example :

`given X = 10 then X > = 11 is false.` 

**<= (Less than or Equal to) :**

this operator checks whether the left side operand value is less than or equal to the right side operand value. If yes then it returns true otherwise it returns false.

Example :

`given X = 10 then X < = 10 is true. `

**Logical Operators :**

**&& (Logical AND) :**

It checks whether two operands are non-zero (0, false, undefined, null or “” are considered as zero), if yes then return 1 otherwise 0.

Example :

```
Y = 5 and X = 6
Y && X is true.
```

**|| (Logical OR) :**

It checks whether any one of the two operands is non-zero (0, false, undefined, null or “” is considered as zero). Thus || returns true if either operand is true and if both are false it returns false.

Example :

```
Y = 5 and X = 0
Y || X is true.
```

**! (Logical NOT) :**

It reverses the boolean result of the operand (or condition).

Example :

```
Y = 5 and X = 0
!(Y || X) is false.
```

**Ternary Operator :**

**: ? Operator :**

It is like the short form of the if-else condition.

Syntax:

`Y =  ? A : B `

where A and B are values and if condition is true thhen Y = A otherwise Y = B.

Example:

```
Y = (6>5) ? 6 : 5
therefore Y = 6
```

typeof Operator: It returns the type of a variable.

Example:

```
<html> 
<head> 
<title> GfG typeof example </title>  
</head> 
<body> 
      
    <script type="text/javascript"> 
            var a = 17; 
            var b = "GeeksforGeeks"; 
            var c = ""; 
            var d = null; 
  
            document.write("Type of a = " + (typeof a)); 
            document.write("<br>"); 
  
            document.write("Type of b = " + (typeof b)); 
            document.write("<br>"); 
  
            document.write("Type of c = " + (typeof c)); 
            document.write("<br>"); 
  
            document.write("Type of d = " + (typeof d)); 
            document.write("<br>"); 
  
            document.write("Type of e = " + (typeof e)); 
            document.write("<br>"); 
    </script> 
</body> 
</html> 
```

Output:

```
Type of a = number
Type of b = string
Type of c = string
Type of d = object
Type of e = undefined
```