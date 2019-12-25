---
image: "/assets/default-social-image.png"
title: JavaScript Rest parameter
categories: JavaScript-operators
---

Rest parameter is a better way to handle function parameters, enabling us to manage various inputs in a system more effectively as parameters. The syntax of the rest parameter helps us to describe as an array of an indefinite number of arguments. A function can be called with any number of arguments with the aid of a rest parameter, no matter how it was specified. In ES2015 or ES6, the rest parameter is introduced to improve the ability to handle parameters.

Syntax:

```
function functionname[...parameters]//... is the rest parameter
{
statement;
}
```

Note: When... is the parameter at the end of the function, it is the rest parameter. It stores as an array, n number of parameters. Let's see how the formula for the rest parameter works:

```
// Without rest parameter 
function fun(a, b){ 
    return a + b; 
} 
console.log(fun(1, 2)); // 3 
console.log(fun(1, 2, 3, 4, 5)); // 3
```

In the above code, even if we pass arguments more than the parameters, no error will be thrown but only the first two arguments will be evaluated. In the case of the rest parameter, it's unique. Using the rest parameter, we will collect as many arguments as possible into an array choose to do with what we want.

Code demonstrating addition of numbers using rest parameter.

```
// es6 rest parameter 
function fun(...input){ 
    let sum = 0; 
    for(let i of input){ 
        sum+=i; 
    } 
    return sum; 
} 
console.log(fun(1,2)); //3 
console.log(fun(1,2,3)); //6 
console.log(fun(1,2,3,4,5)); //15 
```

Once we called the fun() function, we were able to get the sum of all the elements we entered in the argument. The sum of all the elements in the element is calculated by using the for..of loop used to traverse the iterable elements within an array.

Note: The last parameter must be the last argument, as its task is to gather all the remaining arguments in an array. So it doesn't make sense to have a function definition like the code below and will throw an error.

```
// non-sense code 
function fun(a,...b,c){ 
     //code 
     return; 
} 
```

Let's use the rest parameter within a function with some other arguments like:

```
// rest with function and other arguments 
function fun(a,b,...c){ 
    console.log(`${a} ${b}`); //Mukul Latiyan 
    console.log(c);  //[ 'Lionel', 'Messi', 'Barcelona' ] 
    console.log(c[0]); //Lionel 
    console.log(c.length); //3 
    console.log(c.indexOf('Lionel')); //0 
} 
fun('Mukul','Latiyan','Lionel','Messi','Barcelona'); 
```

In the code example above, we passed the rest parameter as the third parameter and then we basically called the fun() function with five arguments and the first two were handled normally and the others were all obtained by the rest parameter and so we get 'Lionel' when we try to access c[0] and it is also important to note that the rest parameter provides an array in return and we can use the array methods offered by the javascript.