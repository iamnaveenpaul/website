---
image: "/assets/default-social-image.png"
title: JavaScript Bitwise Operators
categories: JavaScript-operators
---

JavaScript also allows bit-wise operations like in C, C++, Java, Python and many other languages. A number is registered in JavaScript as a 64-bit floating point integer, but the bit-wise operation is performed on a 32-bit binary number i.e. to execute a bit-operation JavaScript converts the number to a 32-bit binary number (signed) and executes the function and converts the result back to a 64-bit.

For JavaScript, some bit-wise logical operators are used below.

Bit-wise AND (&): a binary operator i.e. two operands are accepted. Bit-wise AND (&) returns 1 if, in any other situation, all bits are set (i.e. 1) and 0.

```
A	B	OUTPUT ( A & B )
0	0	0
0	1	0
1	0	0
1	1	1
```

Bit-Wise OR(|): (it is a binary operator, i.e. two operands are accepted. Bit-wise OR(|) (returns 1 if in any other case one of the operands is set (i.e. 1) and 0.

```
A	B	OUTPUT ( A | B )
0	0	0
0	1	1
1	0	1
1	1	1
```

Bit-Wise XOR (^): it is a binary operator i.e. two operands are accepted. Bit-wise XOR (^) returns 1 if both operands and 0 are different.

```
A	B	OUTPUT ( A ^ B )
0	0	0
0	1	1
1	0	1
1	1	0
```

Bit-Wise NOT(~): It is a single operator, i.e. it accepts individual operands. Bit-wise NOT(~) flips the bits, i.e. 0 is 1 and 1 is 0.

```
A	OUTPUT ( ~A )
0	1
1	0
```

There are a few bit-wise JavaScript shift operators.

Left Shift (<<): a binary operator, i.e. two operands are accepted. The number is defined by the first operator and the amount of bits to be shifted by the second operator. Every bit is shifted to the left, adding 0 bits from the right. The left's leftover pieces was discarded.

```
A	6 ( 00000000000000000000000000000110 )
B	1 ( 00000000000000000000000000000001 )
OUTPUT ( A << B )	12 ( 00000000000000000000000000001100 )
```

Sign Propagating Right Shift (>>): a binary operator, i.e. two operands are accepted. The number is defined by the first operand and the amount of bits to be shifted by the second operand. The excess bits are discarded and every bit is shifted to the right. This is Sign Propagating as the bits added from the left are dependent on the number sign (i.e.0 if positive and 1 if negative).

```
A	6 ( 00000000000000000000000000000110 )
B	1 ( 00000000000000000000000000000001 )
OUTPUT ( A >> B )	3 ( 00000000000000000000000000000011 )
```

Zero fill right shift (>>>): it is a binary operator, i.e. two operands are accepted. The number is defined by the first operand and the amount of bits to be shifted by the second operand. The excess bits are discarded and every bits are shifted to the right. 0 Bit from the left is added to fill the zero right shift.

```
A	6 ( 00000000000000000000000000000110 )
B	1 ( 00000000000000000000000000000001 )
OUTPUT ( A >>> B )	3 ( 00000000000000000000000000000011 )
```

The operators mentioned above are implemented below.

```
<script> 
var a = 6; 
var b = 1; 
  
// AND Operation 
document.write("A & B = " + (a & b) + '<br>'); 
  
  
// OR operation 
document.write("A | B = " + (a | b) + '<br>'); 
  
// NOT operation 
document.write("~A = " + (~a) + '<br>'); 
  
  
// Sign Propagating Right Shift 
document.write("A >> B = " + (a >> b) + '<br>'); 
  
  
// Zero Fill Right Shift 
document.write("A >>> B = " + (a >>> b) + '<br>'); 
  
  
// Left Shift 
document.write("A << B = " + (a << b) + '<br>'); 
</script> 
```

Output:

```
A & B = 0
A | B = 7
~A = -7
A >> B = 3
A >>> B = 3
A << B = 12
```