---
image: "/assets/default-social-image.png"
title: JavaScript ‘===’ vs ‘==’Comparison Operator
categories: JavaScript-operators
---

There are four ways to test equality in Javascript(ES6) that are described below:

* Using ‘==’ operator
* Using ‘===’ operator
* SameValueZero: used mainly in sets, maps and arrays.
* SameValue: used elsewhere

Our main concern now is to get to know the difference that the javascript gives between the '==' and '===' operators, while they look similar, yet they are quite distinct.

'==' operator: The '===' operator in Javascript is also regarded as a loose equality operator, which is used specifically to evaluate two values on both sides and then return true or false. Only after converting all values to a common type i.e. type coercion, this operator tests equality.

Note: Type coercion implies that only after attempting to convert them to the same type will the two values be compared. Let's look at all the value of the operator '==' returning true.

Example:

```
// '==' operator 
console.log(21 == 21); 
console.log(21 == '21'); 
console.log('food is love'=='food is love'); 
console.log(true == 1); 
console.log(false == 0); 
console.log(null == undefined); 
```

In the above code, when we compare 21 with '21', the javascript will convert the '21' into the number value of 21 and thus we get true, something similar happens when we try to check whether 'true == 1' basically converts 1 into a actual true value and then compare and return the true boolean. The case of (null == undefined) is special because we get true when we compare these values,

There are two types of values in javascript: true or false.

**True**

* ‘0’
* ‘false’ // false wrapped in string.
* []
* {}
* function(){}

**False**

* ” or “” // empty string
* false
* 0
* null
* undefined
* NaN // not-a-number

Thus both null and undefined are false values and represent an 'empty' or undefined value in js, hence the '==' operator comparison returns true.

Finally, let's look at all the value the '==' operator returns to is false.

Example:

```
// '==' operator 
console.log(21 == 32); 
console.log(21 == '32'); 
console.log(true == 0); 
console.log(null == false); 
```

If we compare null with false, we get false in the above code, because null is a primitive data type, it can never be equivalent to a boolean value, even though it belongs to the same actual false category.

'===' operator: also known as a strict equality operator, it compares the value as well as the type, which is why the name 'strict equality' is used.

Let's see some coding that returns true to the operator '==='

Example:

```
// '===' operator 
console.log('hello world' === 'hello world'); 
console.log(true === true); 
console.log(5 === 5); 
```

Simply check on both sides the types and values and then simply print out the true or false boolean.

Any scenario that's going to return false

```
// '===' operator 
console.log(true === 1); 
console.log(true === 'true'); 
console.log(5 === '5'); 
```