---
title: Arrow functions in JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript-functions
---

Prerequisite: this in JavaScript, In this article, some more important features have been addressed with 'this' in JavaScript.

**this and Arrow Functions:**

Arrow functions, implemented in ES6, provide a succinct way of writing JavaScript functions.

The fact that it does not bind its own 'this' is another important advantage it provides. In other terms, there is a lexical or abstract definition of the context inside arrow functions.

What it means?

Unlike other functions, the value of this function within the arrow is not based on how it is called or how it is described. This relies only on the context of its enclosure.

Example:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let People = function(person, age) { 
        this.person = person; 
        this.age = age; 
        this.info = function() { 
  
         // logs People 
         document.write(this); 
  
         setTimeout(function() { 
            // here this!=People 
           document.write(this.person + " is " + this.age +  
                                              " years old"); 
          }, 3000); 
        } 
    }  
   let person1 = new People('John', 21); 
  
// logs : undefined is undefined years old after 3 seconds 
person1.info(); 
</script>       
</body> 
</html>
``` 

Output:

```
[object Object] 
undefined is undefined years old
```

The reason we get undefined outputs instead of the right data as output is because the function defined as the callback for setTimeout has a regular invocation of the function and as we know, this implies that its context is set to the global context, and in certain terms the value of 'this' is set to the window object.

This is because, based on their invocation, each regular non-arrow function determines its own 'this' or context. The context of the enclosing objects/function does not influence this tendency to determine their own context instantly.

How we can solve this?

What if the function did not establish its own context seems to be an obvious solution that comes to mind?What if it inherited the info() context as this would mean that this function() gets 'this' as specified in info()

Ok, that's just what arrow functions do. In their enclosing context, they hold the value of 'this'.

That is, if the function specified as callback for setTimeout() was an arrow function, the value of this would be inherited from the enclosing context info() like in the above instance.

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let People = function(person, age) { 
        this.person = person; 
        this.age = age; 
        this.info = function() { 
  
            // logs People 
            document.write(this);  
  
           setTimeout(() => {  
            // arrow function to make lexical "this" binding 
            // here this=People."this" has been inherited 
            document.write(this.person + " is " + this.age  
                                           + " years old"); 
           }, 3000); 
        } 
    }  
let person1 = new People('John', 21); 
  
// logs : John is 21 years old after 3 seconds 
person1.info();  
</script> 
</body> 
</html> 
```

Output:

```
[object Object] 
John is 21 years old
```

Therefore, regardless of whether the arrow function has been called through function invocation or method invocation, it retains its value from its enclosed context. In other terms, 'this' value in arrow function is the same as it was directly outside of it.

If used outside any enclosing function, the global context is inherited by an arrow function, thereby assigning 'this' value to the global object.

**'this' in separated methods:**

If a method is isolated from any object, or placed in a variable, eg: let separate = People.info, it loses its calling object reference.

Mind (after info) the absence of opening and closing parentheses. It means that we do not immediately call the method.

Example:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let People = function(person, age) { 
        this.person = person; 
        this.age = age; 
        this.info = function() { 
  
            // logs People 
            document.write(this + ' '); 
  
            // here this=People 
            document.write(this.person + " is " + this.age +  
                                      " years old" + '<br>'); 
        } 
    } 
  
let person1 
    = new People('John', 21); 
  
// logs : John is 21 years old 
person1.info(); 
  
// separating the method info() from its 
// object by storing it in a variable 
let separated = person1.info; 
  
// logs : undefined is undefined years old 
separated(); 
</script> 
</body> 
</html> 
```

Output:

```
[object Object] John is 21 years old
[object Window] undefined is undefined years old
```

If we detach the info() from the object person1 by individually storing it, we lose all connections to the object person1.

By using 'this' within the separate method, we can no longer access the parent object because the context of the separate method is reset to the global context.

Therefore, we see that 'this' is now applied to the global window object when we call the separated() method.

How to solve this?

An approach for it is to bind an object's value to the method when the method is stored as separately. It means that all references to 'this' even in the 'separated' method apply to this bound object.

Which can be done using bind():

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let People = function(person, age) { 
        this.person = person; 
        this.age = age; 
        this.info = function() { 
  
            // logs People 
            document.write(this + ' '); 
  
            // here this=People 
            document.write(this.person + " is " + this.age +  
                                    " years old" + '<br>'); 
  
        } 
    } 
  
let person1 
    = new People('John', 21); 
  
// logs : John is 21 years old 
person1.info(); 
  
let separated = person1.info.bind(person1); 
  
/* 
the bind(person1) statement ensures that "this" always 
refers to person1 inside the bound method- info() 
*/
  
// logs : undefined is undefined years old 
separated(); 
</script> 
</body> 
</html> 
```

Output:

```
[object Object] John is 21 years old
[object Object] John is 21 years old
```

Note: Instead of code.person1, we could have used any object to bind() to the info() method, and the outputs would have changed accordingly. Binding a method to the parent object is not necessary.

If you've come so far, you'd find we've listed bind() quite a few times.

Now let's analyze what really are bind(), call() and apply().

**bind, call and apply**

bind(), call() and apply() are all used to adjust the function context. Every one of these allows determine the value of 'this' within a function explicitly.

And in how each of them operates, there are some variations. Let's dig at these:

**bind()**

Through binding an object to that function, the method enables us to specifically define what value 'this' will have within a function.

For the function to which it was bound, the bound object serves as the context('this' value).

In order to use it, we specifically need two things – an object to be bound to a function and a function to be bound to 'this' object.

The general bind syntax is as follows:

`boundfunction = someFunction.bind(someObject, additionalParams);`

The first argument used within the bind() directive acts as this value and the accompanying arguments are optional and act as the binding function arguments.

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let fruit = function(person, color) { 
        this.person = person; 
        this.color = color; 
        this.displayInfo = function() { 
            document.write(this.person + " is " + this.color + '<br>'); 
        } 
    } 
  
let bindingObj 
    = { 
        // creating an object using object literal syntax 
        person : "Banana", 
        color : "Yellow", 
      } 
  
// Constructor invocation to create an object fruit1 
let fruit1 
    = new fruit("Orange", "orange"); 
  
// logs :Orange is orange 
// Method invocation of displayInfo() 
fruit1.displayInfo(); 
  
// binding the separated method to a new object 
let newBound = fruit1.displayInfo.bind(bindingObj); 
  
// logs : Banana is Yellow 
newBound(); 
</script> 
</body> 
</html> 
```

Output:

```
Orange is orange
Banana is Yellow
```

Remember that we call displayInfo() on fruit1 using invocation method: fruit1.displayInfo and may assume it to have the fruit1 context. This does not appear to be the case, though, because "Banana is yellow" is logged instead of "Orange is orange"

This is because we specifically bind the value within the displayInfo() to bindingObj using the bind() command.

As we can see, it overrides the usual context laws by binding an object specifically to a function and sets all 'this' values to the bound object within it forcefully.

Sometimes, it lacks its context while passing functions around. For example:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let noBinding = { 
        persons : "John", 
  
        passAround() { 
  
        // displayInfo function is passed 
        // as a callback to setTimeout 
        setTimeout(this.displayInfo, 3000); 
        }, 
  
        displayInfo() { 
  
        // logs the Window object 
        document.write(this + ' '); 
  
        // logs undefined 
        document.write(this.persons); 
  
        } 
    } 
  
    noBinding.passAround(); 
</script> 
</body> 
</html> 
```

Output:

`[object Window] undefined`

In order to prevent context resetting within the function passed as a callback, we specifically bind 'this' value to the same value within passAround(), i.e. to the binding object:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    let binding = { 
        persons : "John", 
  
        passAround() { 
  
            // displayInfo function is passed as a callback  
            // to setTimeout binding the context of displayInfo  
            // to "this" = binding in this execution context 
            setTimeout(this.displayInfo.bind(this), 3000); 
  
        }, 
  
        displayInfo() { 
            // logs the binding object 
            document.write(this + ' '); 
  
            // logs John 
            document.write(this.persons); 
  
        } 
  
    } 
  
     binding.passAround(); 
</script> 
</body> 
</html> 
```

Output:

`[object Object] John`

**call() and apply()**

call() and apply() perform a bind-like role by defining explicitly which value should be placed within a function.

Nonetheless, one major difference between them and bind() is that call() and apply() calls the function directly, rather than merely creating a copy of the function for any possible use with a binding 'this' value.

**The syntax:**

**call:**

`function.call(thisValue, arg1, arg2, ...)`

**apply:**

`function.apply(thisValue, [ arg1, arg2, ...])`

In both instances, the first argument is the value of this that we want the function called to have.

In general, the only distinction between these two methods is the fact that the second argument is an array object of arguments while all arguments are sent in a comma-separated style in call.

Example:

```
<!DOCTYPE html> 
<html> 
<body> 
<script> 
    // Create two different objects to test call() and apply() 
    let banana = { person : 'Banana' }; 
let orange = { person : 'Orange' }; 
function fruits(adj) 
{ 
    document.write(this + ' '); 
    return (this.person + " is " + adj + '<br>'); 
} 
  
  // call() and apply() will immediately invoke 
  // the function they are being called on 
  
  // logs : Banana is yummy 
  document.write(fruits.call(banana, 'yummy')); 
  
 // logs: Orange is sour 
  document.write(fruits.apply(orange, [ 'sour' ])); 
</script> 
</body> 
</html> 
```

Output:

```
[object Object] Banana is yummy
[object Object] Orange is sour
```

Note: The methods accessible on the default Function object prototype are both call() and apply().

**'this' with event listeners**

'this' carries the value of the element that triggered the event within functions used as callbacks for event listeners.

```
<!DOCTYPE html> 
<html> 
<body> 
<button>Click me to see console logging < /button> 
<script> 
    let elem = document.querySelector('btn') 
        elem.addEventListener('click', function() { 
        // logs: btn  
       document.write(this) 
     }) 
</script> 
</body> 
</html> 
```

If the callback function used here is an arrow function and our event listener is nesting in an another method, 'this' would apply to the outer nesting process context and we can no longer access the element that is applied to the event listener using 'this', as we had in the earlier illustration of the program.

Hopefully, using the currentTarget approach on the element, 'this' can be easily solved:

```
<!DOCTYPE html> 
<html> 
<body> 
<button>Click me to see console logging < /button> 
<script> 
function outerfunc(elem) 
{ 
  
    this.clickHandler = function() { 
    elem.addEventListener('click', (e) => { 
  
       // logs the<button />element  
      document.write(e.currentTarget); 
  
   // this has the value of outerfunc 
this.displayInfo(); 
}) 
} 
; 
this.displayInfo = function() { 
    document.write(' Correctly identified!'); 
} 
} 
  
let button = document.body.querySelector('button'); 
let test = new outerfunc(button); 
test.clickHandler() 
</script> 
</body> 
</html> 
```

Output:

`[object HTMLButtonElement] Correctly identified!`

As we're seeing, using the currentTarget helps us to access the element on which the event listener is applied and 'this' enabling us to access the enclosing function context – i.e. 'this' enables us to call the displayInfo() method effectively.