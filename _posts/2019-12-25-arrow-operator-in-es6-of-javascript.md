---
image: "/assets/default-social-image.png"
title: Arrow operator in ES6 of JavaScript
categories: JavaScript-operators
---

ES6 has come with several perks, one of which is the arrow operator. It has reduced the code size function and it is one of the interview's trending issues. Let's have a deeper look into functioning in the arrow operator.

**Syntax:**

The following syntax defines a function in ES5:

```
function functionName(arg1, arg2….)
{
    // body of function
}
```

But in ES6, an arrow operator is used to define a feature and its syntax is as follows:

```
const functionName = (arg1, arg2 ….) => {
    // body of function
}
```

**Advantages of Arrow Operator:**

**1) Reduces Code Size:**

Because we substituted the function with the equivalent arrow operator, the code size is minimized and we need to compose fewer code for the same job. That's why I appreciate the function definition method for the arrow operator.

**2) Drop the Function braces for one line Functions:**

For eg, we may drop the function braces in the declaration of the arrow operator:

**Code #1:**

```
<script> 
  
   //ES5 VERSION 
   var setSize = (sz)=> 
   size=sz; 
     
   //sets size value to the passed value 
   setSize(10); 
   document.write(size); 
                      
</script> 
```

Output:

`10`

Which could also be written as:

**Code #2:**

```
<script> 
  
    //ES6 Version  
    //Do not need to put curly braces for one line functions 
    setDoubleSize = (sz)=>size=2*sz; 
      
    //Sets value of size equivalent to double of 
    //passed argument in setDoubleSize function 
    setDoubleSize(35); 
    document.write(size);     
      
</script> 
```

Output:

`70`

**3) No need to define return statement in one line Functions:**

You have to specify the return statement in the functions in ES5 and if the return statement is not specified in ES6, then ES6 returns the value automatically whenever the function is called.

Which would be more clear as follows:

The one bit left shifting function ES5 version:

```
function leftShift(value) 
{ 
    return value / 2; 
} 
```

While this function can be written as follows in ES6:

`var leftShift = (value) => value / 2; `

**Code #3:**

```
<script> 
  
    //ES5 VERSION 
    function leftShiftES5(value){ 
    return value/2; 
    } 
      
    //ES6 VERSION 
    var leftShiftES6 = (value)=>value/2; 
    var a=10,b=10; 
    document.write('values before left shift'+"<br>"); 
    document.write('a : '+a+' b : '+b + "<br>"); 
  
    //Both of the function should give same output  
    a=leftShiftES5(a); 
    b=leftShiftES6(b); 
    document.write('values after left shift' +"<br>"); 
    document.write('a : '+a+' b : '+b + "<br>"); 
      
</script> 
```

Output:

```
values before left shift
a : 10 b : 10
values after left shift
a : 5 b : 5
```

**4) Lexically bind the context :**

Lexically, the arrow operator binds the context so that it corresponds to the context of origin. It means that it utilizes this from the arrow functions. Let's take a class with an array of age and if we are <18 years of age we must move them into the queue of the child. You must do this in ES5 as follows:

```
this.age.forEach(function(age) { 
    if (age < 18) 
        this.child.push(age); 
}.bind(this)); 
```

The following can be achieved in ES6:

```
this.age.forEach((age) => { 
    if (age < 18) 
        this.child.push(age); 
}); 
```

So we don't have to directly bind it, and this is accomplished by arrow functions automatically, and we've seen arrow function render it less difficult to compose the question to reduce the number of lines and it's being used by the developers being one of the most common questions asked during interviews.