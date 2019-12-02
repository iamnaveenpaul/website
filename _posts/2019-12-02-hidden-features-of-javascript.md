---
title: Hidden Features of JavaScript
image: "/assets/default-social-image.png"
categories: JavaScript
---

**What "Hidden Features" of JavaScript do you think every programmer should know?**

**After having seen the excellent quality of the answers to the following questions I thought it was time to ask it for JavaScript.**

Even though JavaScript is arguably the most important Client Side language right now (just ask Google) it's surprising how little most web developers appreciate how powerful it really is.

**#1.** You don't need to define any parameters for a function. You can just use the function's `arguments` array-like object.

```
function sum() {
    var retval = 0;
    for (var i = 0, len = arguments.length; i < len; ++i) {
        retval += arguments[i];
    }
    return retval;
}

sum(1, 2, 3) // returns 6
```

**#2.** I could quote most of Douglas Crockford's excellent book [JavaScript: The Good Parts](https://rads.stackoverflow.com/amzn/click/com/0596517742).

But I'll take just one for you, always use `===` and `!==` instead of `==` and `!=`

```
alert('' == '0'); //false
alert(0 == ''); // true
alert(0 =='0'); // true
```

`==` is not transitive. If you use `===` it would give false for all of these statements as expected.

**#3.** Functions are first class citizens in JavaScript:

```
var passFunAndApply = function (fn,x,y,z) { return fn(x,y,z); };

var sum = function(x,y,z) {
  return x+y+z;
};

alert( passFunAndApply(sum,3,4,5) ); // 12
```

[Functional programming techniques can be used to write elegant javascript.](http://www.ibm.com/developerworks/library/wa-javascript.html)

Particularly, functions can be passed as parameters, e.g. [Array.filter()](http://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Objects/Array/filter) accepts a callback:

```
[1, 2, -1].filter(function(element, index, array) { return element > 0 });
// -> [1,2]
```

You can also declare a "private" function that only exists within the scope of a specific function:

```
function PrintName() {
    var privateFunction = function() { return "Steve"; };
    return privateFunction();
}
```

**#4.** You can use the **in** operator to check if a key exists in an object:

```
var x = 1;
var y = 3;
var list = {0:0, 1:0, 2:0};
x in list; //true
y in list; //false
1 in list; //true
y in {3:0, 4:0, 5:0}; //true
```

If you find the object literals too ugly you can combine it with the parameterless function tip:

```
function list()
 { var x = {};
   for(var i=0; i < arguments.length; ++i) x[arguments[i]] = 0;
   return x
 }

 5 in list(1,2,3,4,5) //true
```

**#5.**  **Assigning default values to variables**

You can use the logical or operator `||` in an assignment expression to provide a default value:

`var a = b || c;`

The `a` variable will get the value of `c` only if `b` is falsy (if is `null`, `false`, `undefined`, `0`, `empty string`, or `NaN`), otherwise `a` will get the value of `b`.

This is often useful in functions, when you want to give a default value to an argument in case isn't supplied:

```
function example(arg1) {
  arg1 || (arg1 = 'default value');
}
```

Example IE fallback in event handlers:

```
function onClick(e) {
    e || (e = window.event);
}
```

The following language features have been with us for a long time, all JavaScript implementations support them, but they weren't part of the specification until [ECMAScript 5th Edition](http://www.ecma-international.org/publications/standards/Ecma-262.htm):

**The `debugger` statement**

Described in: § 12.15 The debugger statement

This statement allows you to put breakpoints programmatically in your code just by:

```
// ...
debugger;
// ...
```

If a debugger is present or active, it will cause it to break immediately, right on that line.

Otherwise, if the debugger is not present or active this statement has no observable effect.

**Multiline String literals**

Described in: § 7.8.4 String Literals

```
var str = "This is a \
really, really \
long line!";
```

You have to be careful because the character next to the `\` must be a line terminator, if you have a space after the `\` for example, the code will look exactly the same, but it will raise a `SyntaxError`.

**#6.** [JavaScript does not have block scope](http://developer.mozilla.org/En/Core_JavaScript_1.5_Guide:Block_Statement) (but it has [closure](http://developer.mozilla.org/en/Core_JavaScript_1.5_Guide/Functions#Function_expressions) so let's call it even?).

```
var x = 1;
{
   var x = 2;
}
alert(x); // outputs 2
```

**#7.** **You can access object properties with `[]` instead of `.`**

This allows you look up a property matching a variable.

```
obj = {a:"test"};
var propname = "a";
var b = obj[propname];  // "test"
```

You can also use this to get/set object properties whose name is not a legal identifier.

```
obj["class"] = "test";  // class is a reserved word; obj.class would be illegal.
obj["two words"] = "test2"; // using dot operator not possible with the space.
```

Some people don't know this and end up using `eval()` like this, which is a really bad idea:

```
var propname = "a";
var a = eval("obj." + propname);
```

This is harder to read, harder to find errors in (can't use jslint), slower to execute, and can lead to XSS exploits.

**#8.** If you're Googling for a decent JavaScript reference on a given topic, include the "mdc" keyword in your query and your first results will be from the Mozilla Developer Center. I don't carry any offline references or books with me. I always use the "mdc" keyword trick to directly get to what I'm looking for. For example:

Google: [javascript array sort mdc](http://www.google.com/search?q=javascript+array+sort+mdc)
(in most cases you may omit "javascript")

**Update**: Mozilla Developer **Center** has been renamed to Mozilla Developer **Network**. The "mdc" keyword trick still works, but soon enough we may have to **start using "mdn" instead**.

**#9.** Maybe a little obvious to some...

Install [Firebug](http://en.wikipedia.org/wiki/Firebug_(Firefox_extension)) and use `console.log("hello")`. So much better than using random `alert();`'s which I remember doing a lot a few years ago.

**#10.** **Private Methods**

An object can have private methods.

```
function Person(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;

    // A private method only visible from within this constructor
    function calcFullName() {
       return firstName + " " + lastName;    
    }

    // A public method available to everyone
    this.sayHello = function () {
        alert(calcFullName());
    }
}

//Usage:
var person1 = new Person("Bob", "Loblaw");
person1.sayHello();

// This fails since the method is not visible from this scope
alert(person1.calcFullName());
```

**#11.** Also mentioned in Crockford's "Javascript: The Good Parts":

`parseInt()` is dangerous. If you pass it a string without informing it of the proper base it may return unexpected numbers. For example `parseInt('010')` returns 8, not 10. Passing a base to parseInt makes it work correctly:

```
parseInt('010') // returns 8! (in FF3)
parseInt('010', 10); // returns 10 because we've informed it which base to work with.
```

**#12.** Functions are objects and therefore can have properties.

```
fn = function(x) {
   // ...
}

fn.foo = 1;

fn.next = function(y) {
  //
}
```

**#13.** I'd have to say self-executing functions.

`(function() { alert("hi there");})();`

Because Javascript [doesn't have block scope](https://stackoverflow.com/questions/61088/hidden-features-of-javascript/61173#61173), you can use a self-executing function if you want to define local variables:

```
(function() {
  var myvar = 2;
  alert(myvar);
})();
```

Here, `myvar` is does not interfere with or pollute the global scope, and disappears when the function terminates.

**#14.** **Know how many parameters are expected by a function**

```
function add_nums(num1, num2, num3 ){
    return num1 + num2 + num3;
}
add_nums.length // 3 is the number of parameters expected.
```

**Know how many parameters are received by the function**

```
function add_many_nums(){
    return arguments.length;
}    
add_many_nums(2,1,122,12,21,89); //returns 611
```

**#15.** Here are some interesting things:

* Comparing `NaN` with anything (even `NaN`) is always false, that includes `==`, `<` and `>`.
* `NaN` Stands for Not a Number but if you ask for the type it actually returns a number.
* `Array.sort` can take a comparator function and is called by a quicksort-like driver (depends on implementation).
* Regular expression "constants" can maintain state, like the last thing they matched.
* Some versions of JavaScript allow you to access `$0`, `$1`, `$2` members on a regex.
* `null` is unlike anything else. It is neither an object, a boolean, a number, a string, nor `undefined`. It's a bit like an "alternate" `undefined`. (Note: `typeof null == "object"`)
* In the outermost context, `this` yields the otherwise unnameable [Global] object.
* Declaring a variable with `var`, instead of just relying on automatic declaration of the variable gives the runtime a real chance of optimizing access to that variable
* The `with` construct will destroy such optimzations
* Variable names can contain Unicode characters.
* JavaScript regular expressions are not actually regular. They are based on Perl's regexs, and it is possible to construct expressions with lookaheads that take a very, very long time to evaluate.
* Blocks can be labeled and used as the targets of `break`. Loops can be labeled and used as the target of `continue`.
* Arrays are not sparse. Setting the 1000th element of an otherwise empty array should fill it with `undefined`. (depends on implementation)
* `if (new Boolean(false)) {...}` will execute the `{...}` block
* Javascript's regular expression engine's are implementation specific: e.g. it is possible to write "non-portable" regular expressions.

**#16** I know I'm late to the party, but I just can't believe the + operator's usefulness hasn't been mentioned beyond "convert anything to a number". Maybe that's how well hidden a feature it is?

```
// Quick hex to dec conversion:
+"0xFF";              // -> 255

// Get a timestamp for now, the equivalent of `new Date().getTime()`:
+new Date();

// Safer parsing than parseFloat()/parseInt()
parseInt("1,000");    // -> 1, not 1000
+"1,000";             // -> NaN, much better for testing user input
parseInt("010");      // -> 8, because of the octal literal prefix
+"010";               // -> 10, `Number()` doesn't parse octal literals 

// A use case for this would be rare, but still useful in cases
// for shortening something like if (someVar === null) someVar = 0;
+null;                // -> 0;

// Boolean to integer
+true;                // -> 1;
+false;               // -> 0;

// Other useful tidbits:
+"1e10";              // -> 10000000000
+"1e-4";              // -> 0.0001
+"-12";               // -> -12
```

Of course, you can do all this using `Number()` instead, but the `+` operator is so much prettier!

You can also define a numeric return value for an object by overriding the prototype's valueOf() method. Any number conversion performed on that object will not result in NaN, but the return value of the `valueOf()` method:

```
var rnd = {
    "valueOf": function () { return Math.floor(Math.random()*1000); }
};
+rnd;               // -> 442;
+rnd;               // -> 727;
+rnd;               // -> 718;
```

**#17.** "[Extension methods in JavaScript](http://codebetter.com/blogs/jeremy.miller/archive/2008/09/08/quot-extension-method-quot-in-javascript.aspx)" via the prototype property.

```
Array.prototype.contains = function(value) {  
    for (var i = 0; i < this.length; i++) {  
        if (this[i] == value) return true;  
    }  
    return false;  
}
```

This will add a `contains` method to all `Array` objects. You can call this method using this syntax

```
var stringArray = ["foo", "bar", "foobar"];
stringArray.contains("foobar");
```

**#18.** To properly remove a property from an object, you should delete the property instead of just setting it to undefined:

```
var obj = { prop1: 42, prop2: 43 };

obj.prop2 = undefined;

for (var key in obj) {
    ...
```

The property prop2 will still be part of the iteration. If you want to completely get rid of prop2, you should instead do:

`delete obj.prop2;`

The property prop2 will no longer will make an appearance when you're iterating through the properties.

**#19.** `with`.

It's rarely used, and frankly, rarely useful... But, in limited circumstances, it does have its uses.

For instance: object literals are quite handy for quickly setting up properties on a new object. But what if you need to change half of the properties on an existing object?

```
var user = 
{
   fname: 'Rocket', 
   mname: 'Aloysus',
   lname: 'Squirrel', 
   city: 'Fresno', 
   state: 'California'
};

// ...

with (user)
{
   mname = 'J';
   city = 'Frostbite Falls';
   state = 'Minnesota';
}
```

Alan Storm points out that this can be somewhat dangerous: if the object used as context doesn't have one of the properties being assigned to, it will be resolved in the outer scope, possibly creating or overwriting a global variable. This is especially dangerous if you're used to writing code to work with objects where properties with default or empty values are left undefined:

```
var user = 
{
   fname: "John",
// mname definition skipped - no middle name
   lname: "Doe"
};

with (user)
{
   mname = "Q"; // creates / modifies global variable "mname"
}
```

Therefore, it is probably a good idea to avoid the use of the with statement for such assignment.

**See also**: [Are there legitimate uses for JavaScript’s “with” statement?](https://stackoverflow.com/questions/61552/are-there-legitimate-uses-for-javascripts-with-statement)

**#20.** Methods (or functions) can be called on object that are not of the type they were designed to work with. This is great to call native (fast) methods on custom objects.

```
var listNodes = document.getElementsByTagName('a');
listNodes.sort(function(a, b){ ... });
```

This code crashes because `listNodes` is not an `Array`

`Array.prototype.sort.apply(listNodes, [function(a, b){ ... }]);`

This code works because `listNodes` defines enough array-like properties (length, [] operator) to be used by `sort()`.

**#21.** **Prototypal inheritance** (popularized by Douglas Crockford) completely revolutionizes the way you think about loads of things in Javascript.

```
Object.beget = (function(Function){
    return function(Object){
        Function.prototype = Object;
        return new Function;
    }
})(function(){});
```

It's a killer! Pity how almost no one uses it.

It allows you to "beget" new instances of any object, extend them, while maintaining a (live) prototypical inheritance link to their other properties. Example:

```
var A = {
  foo : 'greetings'
};  
var B = Object.beget(A);

alert(B.foo);     // 'greetings'

// changes and additionns to A are reflected in B
A.foo = 'hello';
alert(B.foo);     // 'hello'

A.bar = 'world';
alert(B.bar);     // 'world'


// ...but not the other way around
B.foo = 'wazzap';
alert(A.foo);     // 'hello'

B.bar = 'universe';
alert(A.bar);     // 'world'
```

**#22.** Some would call this a matter of taste, but:

```
aWizz = wizz || "default";
// same as: if (wizz) { aWizz = wizz; } else { aWizz = "default"; }
```

The trinary operator can be chained to act like Scheme's (cond ...):

```
(cond (predicate  (action  ...))
      (predicate2 (action2 ...))
      (#t         default ))
```

can be written as...

```
predicate  ? action( ... ) :
predicate2 ? action2( ... ) :
             default;
```

This is very "functional", as it branches your code without side effects. So instead of:

```
if (predicate) {
  foo = "one";
} else if (predicate2) {
  foo = "two";
} else {
  foo = "default";
}
```

You can write:

```
foo = predicate  ? "one" :
      predicate2 ? "two" :
                   "default";
```

Works nice with recursion, too :)

**#23.** Numbers are also objects. So you can do cool stuff like:

```
// convert to base 2
(5).toString(2) // returns "101"

// provide built in iteration
Number.prototype.times = function(funct){
  if(typeof funct === 'function') {
    for(var i = 0;i < Math.floor(this);i++) {
      funct(i);
    }
  }
  return this;
}


(5).times(function(i){
  string += i+" ";
});
// string now equals "0 1 2 3 4 "

var x = 1000;

x.times(function(i){
  document.body.innerHTML += '<p>paragraph #'+i+'</p>';
});
// adds 1000 parapraphs to the document
```

**#24.** How about **closures** in JavaScript (similar to anonymous methods in C# v2.0+). You can create a function that creates a function or "expression".

Example of **closures**:

```
//Takes a function that filters numbers and calls the function on 
//it to build up a list of numbers that satisfy the function.
function filter(filterFunction, numbers)
{
  var filteredNumbers = [];

  for (var index = 0; index < numbers.length; index++)
  {
    if (filterFunction(numbers[index]) == true)
    {
      filteredNumbers.push(numbers[index]);
    }
  }
  return filteredNumbers;
}

//Creates a function (closure) that will remember the value "lowerBound" 
//that gets passed in and keep a copy of it.
function buildGreaterThanFunction(lowerBound)
{
  return function (numberToCheck) {
    return (numberToCheck > lowerBound) ? true : false;
  };
}

var numbers = [1, 15, 20, 4, 11, 9, 77, 102, 6];

var greaterThan7 = buildGreaterThanFunction(7);
var greaterThan15 = buildGreaterThanFunction(15);

numbers = filter(greaterThan7, numbers);
alert('Greater Than 7: ' + numbers);

numbers = filter(greaterThan15, numbers);
alert('Greater Than 15: ' + numbers);
```

**#25.** You can also **extend (inherit) classes and override properties/methods** using the prototype chain **spoon16** alluded to.

In the following example we create a class Pet and define some properties. We also override the `.toString()` method inherited from Object.

After this we create a Dog class which **extends Pet and overrides the `.toString()`** method again changing it's behavior (polymorphism). In addition we add some other properties to the child class.

After this we check the inheritance chain to show off that Dog is still of type Dog, of type Pet, and of type Object.

```
// Defines a Pet class constructor 
function Pet(name) 
{
    this.getName = function() { return name; };
    this.setName = function(newName) { name = newName; };
}

// Adds the Pet.toString() function for all Pet objects
Pet.prototype.toString = function() 
{
    return 'This pets name is: ' + this.getName();
};
// end of class Pet

// Define Dog class constructor (Dog : Pet) 
function Dog(name, breed) 
{
    // think Dog : base(name) 
    Pet.call(this, name);
    this.getBreed = function() { return breed; };
}

// this makes Dog.prototype inherit from Pet.prototype
Dog.prototype = new Pet();

// Currently Pet.prototype.constructor
// points to Pet. We want our Dog instances'
// constructor to point to Dog.
Dog.prototype.constructor = Dog;

// Now we override Pet.prototype.toString
Dog.prototype.toString = function() 
{
    return 'This dogs name is: ' + this.getName() + 
        ', and its breed is: ' + this.getBreed();
};
// end of class Dog

var parrotty = new Pet('Parrotty the Parrot');
var dog = new Dog('Buddy', 'Great Dane');
// test the new toString()
alert(parrotty);
alert(dog);

// Testing instanceof (similar to the `is` operator)
alert('Is dog instance of Dog? ' + (dog instanceof Dog)); //true
alert('Is dog instance of Pet? ' + (dog instanceof Pet)); //true
alert('Is dog instance of Object? ' + (dog instanceof Object)); //true
```

Both answers to this question were codes modified from a great MSDN article by [Ray Djajadinata](http://msdn.microsoft.com/en-us/magazine/cc163419.aspx).

**#26.** You may catch exceptions depending on their type. Quoted from [MDC](https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Statements/try...catch):

```
try {
   myroutine(); // may throw three exceptions
} catch (e if e instanceof TypeError) {
   // statements to handle TypeError exceptions
} catch (e if e instanceof RangeError) {
   // statements to handle RangeError exceptions
} catch (e if e instanceof EvalError) {
   // statements to handle EvalError exceptions
} catch (e) {
   // statements to handle any unspecified exceptions
   logMyErrors(e); // pass exception object to error handler
}
```

**NOTE**: Conditional catch clauses are a Netscape (and hence Mozilla/Firefox) extension that is not part of the ECMAScript specification and hence cannot be relied upon except on particular browsers.

**#27.** Off the top of my head...

**Functions**

arguments.callee refers to the function that hosts the "arguments" variable, so it can be used to recurse anonymous functions:

```
var recurse = function() {
  if (condition) arguments.callee(); //calls recurse() again
}
```

That's useful if you want to do something like this:

```
//do something to all array items within an array recursively
myArray.forEach(function(item) {
  if (item instanceof Array) item.forEach(arguments.callee)
  else {/*...*/}
})
```

**Objects**

An interesting thing about object members: they can have any string as their names:

```
//these are normal object members
var obj = {
  a : function() {},
  b : function() {}
}
//but we can do this too
var rules = {
  ".layout .widget" : function(element) {},
  "a[href]" : function(element) {}
}
/* 
this snippet searches the page for elements that
match the CSS selectors and applies the respective function to them:
*/
for (var item in rules) {
  var elements = document.querySelectorAll(rules[item]);
  for (var e, i = 0; e = elements[i++];) rules[item](e);
}
```

**Strings**

String.split can take regular expressions as parameters:

```
"hello world   with  spaces".split(/\s+/g);
//returns an array: ["hello", "world", "with", "spaces"]
```

String.replace can take a regular expression as a search parameter and a function as a replacement parameter:

```
var i = 1;
"foo bar baz ".replace(/\s+/g, function() {return i++});
//returns "foo1bar2baz3"
```

**#28.** You can use objects instead of switches most of the time.

```
function getInnerText(o){
    return o === null? null : {
        string: o,
        array: o.map(getInnerText).join(""),
        object:getInnerText(o["childNodes"])
    }[typeis(o)];
}
```

Update: if you're concerned about the cases evaluating in advance being inefficient (why are you worried about efficiency this early 
on in the design of the program??) then you can do something like this:

```
function getInnerText(o){
    return o === null? null : {
        string: function() { return o;},
        array: function() { return o.map(getInnerText).join(""); },
        object: function () { return getInnerText(o["childNodes"]; ) }
    }[typeis(o)]();
}
```

This is more onerous to type (or read) than either a switch or an object, but it preserves the benefits of using an object instead of a switch, detailed in the comments section below. This style also makes it more straightforward to spin this out into a proper "class" once it grows up enough.

update2: with proposed syntax extensions for ES.next, this becomes

```
let getInnerText = o -> ({
    string: o -> o,
    array: o -> o.map(getInnerText).join(""),
    object: o -> getInnerText(o["childNodes"])
}[ typeis o ] || (->null) )(o);
```

**#29.** Be sure to use the **hasOwnProperty** method when iterating through an object's properties:

```
for (p in anObject) {
    if (anObject.hasOwnProperty(p)) {
        //Do stuff with p here
    }
}
```

This is done so that you will only access the **direct properties of anObject**, and not use the properties that are down the prototype chain.

**#30.** Private variables with a Public Interface

It uses a neat little trick with a self-calling function definition. Everything inside the object which is returned is available in the public interface, while everything else is private.

```
var test = function () {
    //private members
    var x = 1;
    var y = function () {
        return x * 2;
    };
    //public interface
    return {
        setx : function (newx) {
            x = newx;
        },
        gety : function () {
            return y();
        }
    }
}();

assert(undefined == test.x);
assert(undefined == test.y);
assert(2 == test.gety());
test.setx(5);
assert(10 == test.gety());
```

**#31.** Timestamps in JavaScript:

```
// Usual Way
var d = new Date();
timestamp = d.getTime();

// Shorter Way
timestamp = (new Date()).getTime();

// Shortest Way
timestamp = +new Date();
```

**#32.** You can assign local variables using [] on the left hand side. Comes in handy if you want to return more than one value from a function without creating a needless array.

```
function fn(){
    var cat = "meow";
    var dog = "woof";
    return [cat,dog];
};

var [cat,dog] = fn();  // Handy!

alert(cat);
alert(dog);
```

**#33.** All objects in Javascript are implemented as hashtables, so their properties can be accessed through the indexer and vice-versa. Also, you can enumerate all the properties using the **for/in** operator:

```
var x = {a: 0};
x["a"]; //returns 0

x["b"] = 1;
x.b; //returns 1

for (p in x) document.write(p+";"); //writes "a;b;"
```

**#34.** When you want to remove an element from an array, one can use the **delete** operator, as such:

```
var numbers = [1,2,3,4,5];
delete numbers[3];
//numbers is now [1,2,3,undefined,5]
```

As you can see, the element was removed, but a hole was left in the array since the element was replaced with an undefined value.

Thus, to work around this problem, instead of using delete, use the **splice** array method...as such:

```
var numbers = [1,2,3,4,5];
numbers.splice(3,1);
//numbers is now [1,2,3,5]
```

The first argument of **splice** is an ordinal in the array [index], and the second is the number of elements to delete.

**#35.** There are several answers in this thread showing how to extend the Array object via its prototype. This is a BAD IDEA, because it breaks the `for (i in a)` statement.

So is it okay if you don't happen to use `for (i in a)` anywhere in your code? Well, only if your own code is the only code that you are running, which is not too likely inside a browser. I'm afraid that if folks start extending their Array objects like this, Stack Overflow will start overflowing with a bunch of mysterious JavaScript bugs.

See helpful details [here](http://web-graphics.com/2006/05/23/on-modifying-prototypes-of-javascript-built-ins/).

**#36.** In a function, you can return the function itself:

```
function showSomething(a){
   alert(a);
   return arguments.callee;
}

// Alerts: 'a', 'b', 'c'
showSomething('a')('b')('c');

// Or what about this:
(function (a){
   alert(a);
   return arguments.callee;
})('a')('b')('c');
```

I don't know when it could be useful, anyway, it's pretty weird and fun:

```
var count = function(counter){
   alert(counter);
   if(counter < 10){
      return arguments.callee(counter+1);
   }
   return arguments.callee;
};

count(5)(9); // Will alert 5, 6, 7, 8, 9, 10 and 9, 10
```

Actually, the [FAB framework](https://github.com/jed/fab) for Node.js seems to have implemented this feature; see [this topic](https://stackoverflow.com/questions/3799238/javascript-fab-framework-on-node-js) for example.

**#37.** The way JavaScript works with `Date()` just excites me!

```
function isLeapYear(year) {
    return (new Date(year, 1, 29, 0, 0).getMonth() != 2);
}
```

This is really "hidden feature".

Edit: Removed "?" condition as suggested in comments for politcorrecteness. Was: ... new Date(year, 1, 29, 0, 0).getMonth() != 2 ? true : false ... Please look at comments for details.

**#38.** My favorite trick is using `apply` to perform a callback to an object's method and maintain the correct "this" variable.

```
function MakeCallback(obj, method) {
    return function() {
        method.apply(obj, arguments);
    };
}

var SomeClass = function() { 
     this.a = 1;
};
SomeClass.prototype.addXToA = function(x) {
     this.a = this.a + x;
};

var myObj = new SomeClass();

brokenCallback = myObj.addXToA;
brokenCallback(1); // Won't work, wrong "this" variable
alert(myObj.a); // 1


var myCallback = MakeCallback(myObj, myObj.addXToA);
myCallback(1);  // Works as expected because of apply
alert(myObj.a); // 2
```

**#39.** Here's a couple of shortcuts:

```
var a = []; // equivalent to new Array()
var o = {}; // equivalent to new Object()
```

**#40.** **The Zen of Closures**

Other people have mentioned closures. But it's surprising how many people know about closures, write code using closures, yet still have the wrong perception of what closures really are. Some people confuse first-class functions with closures. Yet others see it as a kind of static variable.

To me a closure is a kind of 'private' global variable. That is, a kind of variable that some functions see as global but other functions can't see. Now, I know this is playing fast and loose with the description of the underlying mechanism but that is how it feels like and behaves. To illustrate:

```
// Say you want three functions to share a single variable:

// Use a self-calling function to create scope:
(function(){

    var counter = 0; // this is the variable we want to share;

    // Declare global functions using function expressions:
    increment = function(){
        return ++counter;
    }
    decrement = function(){
        return --counter;
    }
    value = function(){
        return counter;
    }
})()
```

now the three function `increment`, `decrement` and `value` share the variable `counter` without `counter` being an actual global variable. This is the true nature of closures:

```
increment();
increment();
decrement();
alert(value()); // will output 1
```

The above is not a really useful use of closures. In fact, I'd say that using it this way is an anti-pattern. But it is useful in understanding the nature of closures. For example, most people get caught when they try to do something like the following:

```
for (var i=1;i<=10;i++) {
    document.getElementById('span'+i).onclick = function () {
        alert('this is span number '+i);
    }
}
// ALL spans will generate alert: this span is span number 10
```

That's because they don't understand the nature of closures. They think that they are passing the value of `i` into the functions when in fact the functions are sharing a single variable `i`. Like I said before, a special kind of global variable.

To get around this you need detach* the closure:

```
function makeClickHandler (j) {
    return function () {alert('this is span number '+j)};
}

for (var i=1;i<=10;i++) {
    document.getElementById('span'+i).onclick = makeClickHandler(i);
}
// this works because i is passed by reference 
// (or value in this case, since it is a number)
// instead of being captured by a closure
```

*note: I don't know the correct terminology here.

**#41.** You never have to use `eval()` to assemble global variable names.

That is, if you have several globals (for whatever reason) named `spec_grapes, spec_apples`, you do not have to access them with `eval("spec_" + var)`.

All globals are members of `window[]`, so you can do `window["spec_" + var]`.

**#42.** JavaScript uses a simple object literal:

`var x = { intValue: 5, strValue: "foo" };`

This constructs a full-fledged object.

JavaScript uses prototype-based object orientation and provides the ability to extend types at runtime:

```
String.prototype.doubleLength = function() {
    return this.length * 2;
}

alert("foo".doubleLength());
```

An object delegates all access to attributes that it doesn't contain itself to its "prototype", another object. This can be used to implement inheritance, but is actually more powerful (even if more cumbersome):

```
/* "Constructor" */
function foo() {
    this.intValue = 5;
}

/* Create the prototype that includes everything
 * common to all objects created be the foo function.
 */
foo.prototype = {
    method: function() {
        alert(this.intValue);
    }
}

var f = new foo();
f.method();
```

**#43.** Prevent annoying errors while testing in Internet Explorer when using `console.log()` for Firebug:

```
function log(message) {
    (console || { log: function(s) { alert(s); }).log(message);
}
```

**#44.** One of my favorites is constructor type checking:

```
function getObjectType( obj ) {  
    return obj.constructor.name;  
}  

window.onload = function() {  
    alert( getObjectType( "Hello World!" ) );  
    function Cat() {  
        // some code here...  
    }  
    alert( getObjectType( new Cat() ) );  
}
```

So instead of the tired old [Object object] you often get with the typeof keyword, you can actually get real object types based upon the constructor.

Another one is using variable arguments as a way to "overload" functions. All you are doing is using an expression to detect the number of arguments and returning overloaded output:

```
function myFunction( message, iteration ) {  
    if ( arguments.length == 2 ) {  
        for ( i = 0; i < iteration; i++ ) {  
            alert( message );  
        }  
    } else {  
        alert( message );  
    }  
}  

window.onload = function() {  
    myFunction( "Hello World!", 3 );  
}
```

Finally, I would say assignment operator shorthand. I learned this from the source of the jQuery framework... the old way:

```
var a, b, c, d;
b = a;
c = b;
d = c;
```

The new (shorthand) way:

```
var a, b, c, d;
d = c = b = a;
```

Good fun :)

**#45.** The fastest loops in JavaScript are `while(i--)` ones. In all browsers. So if it's not that important for order in which elements of your loop get processed you should be using `while(i--)` form:

```
var names = new Array(1024), i = names.length;
while(i--)
  names[i] = "John" + i;
```

Also, if you have to use for() loop going forward, remember always to cache .length property:

```
var birds = new Array(1024); 
for(var i = 0, j = birds.length; i < j; i++)
  birds[i].fly();
```

To join large strings use Arrays (it's faster):

```
var largeString = new Array(1024), i = largeString.length;
while(i--) {
  // It's faster than for() loop with largeString.push(), obviously :)
  largeString[i] = i.toString(16);
}

largeString = largeString.join("");
```

It's much faster than largeString += "something" inside an loop.

**#46.** You can do almost anything between parentheses if you separate statements with commas:

```
var z = ( x = "can you do crazy things with parenthesis", ( y = x.split(" "), [ y[1], y[0] ].concat( y.slice(2) ) ).join(" ") )

alert(x + "\n" + y + "\n" + z)
```

Output:

```
can you do crazy things with parenthesis
can,you,do,crazy,things,with,parenthesis
you can do crazy things with parenthesis
```

**#47.** The concept of truthy and falsy values. You don't need to do something like

`if(someVar === undefined || someVar === null) ...`

Simply do:

`if(!someVar).`

Every value has a corresponding boolean representation.

**#48.** Function statements and function expressions are handled differently.

```
function blarg(a) {return a;} // statement
bleep = function(b) {return b;} //expression
```

All function statements are parsed before code is run - a function at the bottom of a JavaScript file will be available in the first statement. On the other hand, it won't be able to take advantage of certain dynamic context, such as surrounding `with` statements - the `with` hasn't been executed when the function is parsed.

Function expressions execute inline, right where they are encountered. They aren't available before that time, but they can take advantage of dynamic context.

**#49.** `window.name`'s value persists across page changes, can be read by the parent window if in same domain (if in an iframe, use `document.getElementById("your frame's ID").contentWindow.name` to access it), and is limited only by available memory.

**#50.** The parentheses are optional when creating new "objects".

```
function Animal () {

}

var animal = new Animal();
var animal = new Animal;
```

Same thing.

**#51.** Javascript has static variables inside functions:

```
function someFunction(){
  var Static = arguments.callee;
  Static.someStaticVariable = (Static.someStaticVariable || 0) + 1;
  alert(Static.someStaticVariable);
}
someFunction() //Alerts 1
someFunction() //Alerts 2
someFunction() //Alerts 3
```

It also has static variables inside Objects:

```
function Obj(){
  this.Static = arguments.callee;
}
a = new Obj();
a.Static.name = "a";
b = new Obj();
alert(b.Static.name); //Alerts b
```

**#52.** All functions are actually instances of the built-in **Function** type, which has a constructor that takes a string containing the function definition, so you can actually define functions at run-time by e.g., concatenating strings:

```
//e.g., createAddFunction("a","b") returns function(a,b) { return a+b; }
function createAddFunction(paramName1, paramName2)
 { return new Function( paramName1, paramName2
                       ,"return "+ paramName1 +" + "+ paramName2 +";");
 }
```

Also, for user-defined functions, `Function.toString()` returns the function definition as a literal string.

**#53.** You can execute an object's method on any object, regardless of whether it has that method or not. Of course it might not always work (if the method assumes the object has something it doesn't), but it can be extremely useful. For example:

```
function(){
    arguments.push('foo') // This errors, arguments is not a proper array and has no push method
    Array.prototype.push.apply(arguments, ['foo']) // Works!
}
```

**#54.** The `==` operator has a very special property, that creates this disturbing equality (Yes, I know in other dynamic languages like Perl this behavior would be expected but JavaScript ususally does not try to be smart in comparisons):

```
>>> 1 == true
true
>>> 0 == false
true
>>> 2 == true
false
```

**#55.** `let`.

Counterpart to [var's lack of block-scoping](https://stackoverflow.com/questions/61088/hidden-features-of-javascript#61173) is `let`, [introduced in JavaScript 1.7](http://developer.mozilla.org/en/New_in_JavaScript_1.7#Block_scope_with_let).

* The let statement provides a way to associate values with variables within the scope of a block, without affecting the values of like-named variables outside the block.
* The let expression lets you establish variables scoped only to a single expression.
* The let definition defines variables whose scope is constrained to the block in which they're defined. This syntax is very much like the syntax used for var.
* You can also use let to establish variables that exist only within the context of a for loop.
 
```
 function varTest() {
        var x = 31;
    if (true) {
      var x = 71;  // same variable!
      alert(x);  // 71
    }
    alert(x);  // 71
  }

  function letTest() {
    let x = 31;
    if (true) {
      let x = 71;  // different variable
      alert(x);  // 71
    }
    alert(x);  // 31
  }
```

As of 2008, JavaScript 1.7 is supported in FireFox 2.0+ and Safari 3.x.

**#56.** If you blindly `eval()` a JSON string to deserialize it, you may run into problems:

* It's not secure. The string may contain malicious function calls!
* If you don't enclose the JSON string in parentheses, property names can be mistaken as labels, resulting in unexpected behaviour or a syntax error:

```
eval("{ \"foo\": 42 }"); // syntax error: invalid label
eval("({ \"foo\": 42 })"); // OK
```

**#57.** You can turn "any* object with integer properties, and a length property into an array proper, and thus endow it with all array methods such as push, pop, splice, map, filter, reduce, etc.

`Array.prototype.slice.call({"0":"foo", "1":"bar", 2:"baz", "length":3 }) `

// returns ["foo", "bar", "baz"]

This works with jQuery objects, html collections, and Array objects from other frames (as one possible solution to the whole array type thing). I say, if it's got a length property, you can turn it into an array and it doesn't matter. There's lots of non array objects with a length property, beyond the arguments object.

**#58.** If you're attempting to sandbox javascript code, and disable every possible way to evaluate strings into javascript code, be aware that blocking all the obvious eval/document.write/new Function/setTimeout/setInterval/innerHTML and other DOM manipulations isn't enough.

Given any object o, `o.constructor.constructor("alert('hi')")()` will bring up an alert dialog with the word "hi" in it.

You could rewrite it as

```
var Z="constructor";
Z[Z][Z]("alert('hi')")();
Fun stuff.
```

**#59.** Microsofts [gift to JavaScript](http://en.wikipedia.org/wiki/XMLHttpRequest): AJAX

```
AJAXCall('http://www.abcd.com/')

function AJAXCall(url) {
 var client = new XMLHttpRequest();
 client.onreadystatechange = handlerFunc;
 client.open("GET", url);
 client.send();
}

function handlerFunc() {
 if(this.readyState == 4 && this.status == 200) {
 if(this.responseXML != null)
   document.write(this.responseXML)
 }
}
```

**#60.** **The [Module Pattern](http://yuiblog.com/blog/2007/06/12/module-pattern/)**

```
<script type="text/javascript">
(function() {

function init() {
  // ...
}

window.onload = init;
})();
</script>
```

Variables and functions declared without the var statement or outside of a function will be defined in the global scope. If a variable/function of the same name already exists it will be silently overridden, which can lead to very hard to find errors. A common solution is to wrap the whole code body into an anonymous function and immediately execute it. This way all variables/functions are defined in the scope of the anonymous function and don't leak into the global scope.

To explicitly define a variable/function in the global scope they have to be prefixed with window:

```
window.GLOBAL_VAR = 12;
window.global_function = function() {};
```

**#61.** This is a hidden feature of jQuery, not Javascript, but since there will never be a "hidden features of jQuery" question...

You can define your own `:something` selectors in jQuery:

```
$.extend($.expr[':'], {
  foo: function(node, index, args, stack) {
    // decide if selectors matches node, return true or false
  }
});
```

For selections using `:foo`, such as `$('div.block:foo("bar,baz") span')`, the function `foo` will be called for all nodes which match the already processed part of the selector. The meaning of the arguments:

1. `node` holds the current node
2. `index` is the index of the node in the node set
3. `args` is an array that is useful if the selector has an argument or multiple names:
4. `stack` is the node set (an array holding all nodes which are matched at that point)

* `args[0]` is the whole selector text (e.g. `:foo("bar, baz")`)
* `args[1]` is the selector name (e.g. `foo`)
* `args[2]` is the quote character used to wrap the argument (e.g. `"` for `:foo("bar, baz")`) or an empty string if there is no quoting (`:foo(bar, baz)`) or undefined if there is no argument
* `args[3]` is the argument, including any quotes, (e.g. `"bar, baz"`) or undefined if there are no arguments

The function should return `true` if the selector matches, false otherwise.

For example, the following code will enable selecting nodes based on a full-text regexp search:

```
$.extend($.expr[':'], {
  matches: function(node, index, args, stack) {
    if (!args.re) { // args is a good place for caching
      var re = args[3];
      if (args[2]) { // get rid of quotes
        re = re.slice(1,-1);
      }
      var separator = re[0];
      var pos = re.lastIndexOf(separator);
      var modifiers = re.substr(pos+1);
      var code = re.substr(1, pos-1);
      args.re = new RegExp(code, modifiers);
    }
    return $(node).text().match(args.re);
  }
});

// find the answers on this page which contain /**/-style comments
$('.answer .post-text code:matches(!/\\*[\\s\\S]*\\*/!)');
```

You could reach a similar effect with the callback version of `[.filter()](http://api.jquery.com/filter/)`, but custom selectors are much more flexible and usually more readable.

**#62.** `Function.toString()` (implicit):

```
function x() {
    alert("Hello World");
}
eval ("x = " + (x + "").replace(
    'Hello World',
    'STACK OVERFLOW BWAHAHA"); x("'));
x();
```

**#63.** [Generators and Iterators](http://developer.mozilla.org/en/New_in_JavaScript_1.7#Generators_and_iterators) (works only in Firefox 2+ and Safari).

```
function fib() {
  var i = 0, j = 1;
  while (true) {
    yield i;
    var t = i;
    i = j;
    j += t;
  }
}

var g = fib();
for (var i = 0; i < 10; i++) {
  document.write(g.next() + "<br>\n");
}
```

The function containing the `yield` keyword is a generator. When you call it, its formal parameters are bound to actual arguments, but its body isn't actually evaluated. Instead, a generator-iterator is returned. Each call to the generator-iterator's `next()` method performs another pass through the iterative algorithm. Each step's value is the value specified by the `yield` keyword. Think of `yield` as the generator-iterator version of return, indicating the boundary between each iteration of the algorithm. Each time you call `next()`, the generator code resumes from the statement following the `yield`.

In normal usage, iterator objects are "invisible"; you won't need to operate on them explicitly, but will instead use JavaScript's `for...in` and `for each...in` statements to loop naturally over the keys and/or values of objects.

```
var objectWithIterator = getObjectSomehow();

for (var i in objectWithIterator)
{
  document.write(objectWithIterator[i] + "<br>\n");
}
```

**#64.** Visit:

* [http://images.google.com/images?q=disco](http://images.google.com/images?q=disco)

Paste this JavaScript code into your web browser's address bar:

* [http://amix.dk/upload/awt/spin.txt](http://amix.dk/upload/awt/spin.txt)
* [http://amix.dk/upload/awt/disco.txt](http://amix.dk/upload/awt/disco.txt)

Enjoy the JavaScript disco show :-p

**#65.** `undefined` is undefined. So you can do this:

`if (obj.field === undefined) /* ... */`

**#66.** This one is super hidden, and only occasionally useful ;-)

You can use the prototype chain to create an object that delegates to another object without changing the original object.

```
var o1 = { foo: 1, bar: 'abc' };
function f() {}
f.prototype = o1;
o2 = new f();
assert( o2.foo === 1 );
assert( o2.bar === 'abc' );
o2.foo = 2;
o2.baz = true;
assert( o2.foo === 2 );
// o1 is unchanged by assignment to o2
assert( o1.foo === 1 );
assert( o2.baz );
```

This only covers 'simple' values on o1. If you modify an array or another object, then the prototype no longer 'protects' the original object. Beware anytime you have an {} or [] in a Class definition/prototype.

**#67.** All your "hidden" features are right here on the Mozilla wiki: [http://developer.mozilla.org/en/JavaScript](http://developer.mozilla.org/en/JavaScript).

There's [the core JavaScript 1.5 reference](http://developer.mozilla.org/en/Core_JavaScript_1.5_Reference), [what's new in JavaScript 1.6](http://developer.mozilla.org/en/New_in_JavaScript_1.6), [what's new in JavaScript 1.7](http://developer.mozilla.org/en/New_in_JavaScript_1.7), and also [what's new in JavaScript 1.8](http://developer.mozilla.org/en/New_in_JavaScript_1.8). Look through all of those for examples that actually work and are not wrong.

**#68.** **[Namespaces](http://www.dustindiaz.com/namespace-your-javascript/)**

In larger JavaScript applications or frameworks it can be useful to organize the code in namespaces. JavaScript doesn't have a module or namespace concept buildin but it is easy to emulate using JavaScript objects. This would create a namespace called `ns` and attaches the function `foo` to it.

```
if (!window.ns) {
  window.ns = {};
}

window.ns.foo = function() {};
```

It is common to use the same global namespace prefix throughout a project and use sub namespaces for each JavaScript file. The name of the sub namespace often matches the file's name.

The header of a file called ns/button.jscould look like this:

```
if (!window.ns) {
  window.ns = {};
}
if (!window.ns.button) {
  window.ns.button = {};
}

// attach methods to the ns.button namespace
window.ns.button.create = function() {};
```

**#69.** **jQuery and JavaScript:**

Variable-names can contain a number of odd characters. I use the $ character to identify variables containing jQuery objects:

```
var $links = $("a");

$links.hide();
```

jQuery's pattern of chaining objects is quite nice, but applying this pattern can get a bit confusing. Fortunately JavaScript allows you to break lines, like so:

```
$("a")
.hide()
.fadeIn()
.fadeOut()
.hide();
```

**General JavaScript:**

I find it useful to emulate scope by using self-executing functions:

```
function test()
{
    // scope of test()

    (function()
    {
        // scope inside the scope of test()
    }());

    // scope of test()
}
```

**#70.** These are not always a good idea, but you can convert most things with terse expressions. The important point here is that not every value in JavaScript is an object, so these expressions will succeed where member access on non-objects like null and undefined will fail. Particularly, beware that `typeof null == "object"`, but you can't `null.toString()`, or ("name" in null).

Convert anything to a Number:

```
+anything
Number(anything)
```

Convert anything to an unsigned four-byte integer:

`anything >>> 0`

Convert anything to a String:

```
'' + anything
String(anything)
```

Convert anything to a Boolean:

```
!!anything
Boolean(anything)
```

Also, using the type name without "new" behaves differently for String, Number, and Boolean, returning a primitive number, string, or boolean value, but with "new" these will returned "boxed" object types, which are nearly useless.

**#71.** It's surprising how many people don't realize that it's object oriented as well.

**#72.** Large loops are faster in `while`-condition and backwards - that is, if the order of the loop doesn't matter to you. In about 50% of my code, it usually doesn't.

i.e.

```
var i, len = 100000;

for (var i = 0; i < len; i++) {
  // do stuff
}
```

Is slower than:

```
i = len;
while (i--) {
  // do stuff
}
```

**#73.** [Joose](http://code.google.com/p/joose-js/) is a nice object system if you would like Class-based OO that feels somewhat like CLOS.

```
// Create a class called Point
Class("Point", {
    has: {
        x: {
            is:   "rw",
            init: 0
        },
        y: {
            is:   "rw",
            init: 0
        }
    },
    methods: {
        clear: function () {
            this.setX(0);
            this.setY(0);
        }
    }
})

// Use the class
var point = new Point();
point.setX(10)
point.setY(20);
point.clear();
```

**#74.** **Syntactic sugar: in-line for-loop closures**

```
var i;

for (i = 0; i < 10; i++) (function ()
{
    // do something with i
}());
```

Breaks almost all of Douglas Crockford's code-conventions, but I think it's quite nice to look at, never the less :)

Alternative:

```
var i;

for (i = 0; i < 10; i++) (function (j)
{
    // do something with j
}(i));
```

**#75.** JavaScript `typeof` operator used with arrays or nulls always returns `object` value which in some cases may not be what programmer would expect.

Here's a function that will return proper values for those items as well. Array recognition was copied from Douglas Crockford's book "JavaScript: The Good Parts".

```
function typeOf (value) {
    var type = typeof value;
    if (type === 'object') {
        if (value === null) {
             type = 'null';
        } else if (typeof value.length === 'number' && 
            typeof value.splice === 'function' && 
            !value.propertyIsEnumerable('length')) {
            type = 'array';
        }
    }
    return type;
}
```

**#76.** **You can iterate over Arrays using "for in"**

Mark Cidade pointed out the usefullness of the "for in" loop :

```
// creating an object (the short way, to use it like a hashmap)
var diner = {
"fruit":"apple"
"veggetable"="bean"
}

// looping over its properties
for (meal_name in diner ) {
    document.write(meal_name+"<br \n>");
}
```

Result :

```
fruit
veggetable
```

But there is more. Since you can use an object like an associative array, you can process keys and values, just like a foreach loop :

```
// looping over its properties and values
for (meal_name in diner ) {
    document.write(meal_name+" : "+diner[meal_name]+"<br \n>");
}
```

Result :

```
fruit : apple
veggetable : bean
```

And since Array are objects too, you can iterate other array the exact same way :

```
var my_array = ['a', 'b', 'c'];
for (index in my_array ) {
    document.write(index+" : "+my_array[index]+"<br \n>");
}
```

Result :

```
0 : a
1 : b
3 : c
```

You can remove easily an known element from an array

```
var arr = ['a', 'b', 'c', 'd'];
var pos = arr.indexOf('c');
pos > -1 && arr.splice( pos, 1 );
```

**You can shuffle easily an array**

`arr.sort(function() Math.random() - 0.5);` – not really random distribution

**#77.** Existence checks. So often I see stuff like this

var a = [0, 1, 2];

```
// code that might clear the array.

if (a.length > 0) {
 // do something
}
```

instead for example just do this:

```
var a = [0, 1, 2];

// code that might clear the array.

if (a.length) { // if length is not equal to 0, this will be true
 // do something
}
```

There's all kinds of existence checks you can do, but this was just a simple example to illustrate a point

Here's an example on how to use a default value.

```
function (someArgument) {
      someArgument || (someArgument = "This is the deault value");
}
```

That's my two cents. There's other nuggets, but that's it for now.

**#78.** Maybe one of the lesser-known ones:

`arguments.callee.caller + Function#toString()`

```
function called(){
    alert("Go called by:\n"+arguments.callee.caller.toString());
}

function iDoTheCall(){
    called();
}

iDoTheCall();
```

Prints out the source code of `iDoTheCall` -- Deprecated, but can be useful sometimes when alerting is your only option....

**#79.** There is also an almost unknown JavaScript syntax:

```
var a;
a=alert(5),7;
alert(a);    // alerts undefined
a=7,alert(5);
alert(a);    // alerts 7

a=(3,6);
alert(a);    // alerts 6
```

More about this [here](https://stackoverflow.com/questions/476218/javascript-syntax-of-a-object-object).

**#80.** As Marius already pointed, you can have public static variables in functions.

I usually use them to create functions that are executed only once, or to cache some complex calculation results.

Here's the example of my old "singleton" approach:

```
var singleton = function(){ 

  if (typeof arguments.callee.__instance__ == 'undefined') { 

    arguments.callee.__instance__ = new function(){

      //this creates a random private variable.
      //this could be a complicated calculation or DOM traversing that takes long
      //or anything that needs to be "cached"
      var rnd = Math.random();

      //just a "public" function showing the private variable value
      this.smth = function(){ alert('it is an object with a rand num=' + rnd); };

   };

  }

  return arguments.callee.__instance__;

};


var a = new singleton;
var b = new singleton;

a.smth(); 
b.smth();
```

As you may see, in both cases the constructor is run only once.

For example, I used this approach back in 2004 when I had to create a modal dialog box with a gray background that covered the whole page (something like [Lightbox](http://en.wikipedia.org/wiki/Lightbox_(JavaScript))). Internet Explorer 5.5 and 6 have the highest stacking context for `<select>` or `<iframe>` elements due to their "windowed" nature; so if the page contained select elements, the only way to cover them was to create an iframe and position it "on top" of the page. So the whole script was quite complex and a little bit slow (it used filter: expressions to set opacity for the covering iframe). The "shim" script had only one `".show()"` method, which created the shim only once and cached it in the static variable :)

**#81.** Hm, I didn't read the whole topic though it's quite interesting for me, but let me make a little donation:

```
// forget the debug alerts
var alertToFirebugConsole = function() {
    if ( window.console && window.console.log ) {
        window.alert = console.log;
    }
}
```

**#82.** This seems to only work on Firefox (SpiderMonkey). Inside a function:

* `arguments[-2]` gives the number of arguments (same as `arguments.length`)
* `arguments[-3]` gives the function that was called (same as `arguments.callee`)

**#83.** JavaScript is considered to be very good at exposing all its object so no matter if its window object itself.

So if i would like to override the browser alert with JQuery/YUI div popup which too accepts string as parameter it can be done simply using following snippet.

```
function divPopup(str)
{
    //code to show the divPopup
}
window.alert = divPopup;
```

With this change all the calls to the `alert()` will show the good new div based popup instead of the browser specific alert.

**#84.** **JavaScript versatility - Overriding default functionality**

Here's the code for overriding the `window.alert` function with jQuery UI's [Dialog widget](http://jqueryui.com/demos/dialog/). I did this as a jQuery plug-in. And you can read about it on my blog; [altAlert, a jQuery plug-in for personalized alert messages](http://roosteronacid.com/blog/index.php/2010/01/20/jquery-plug-in-personalized-alert-messages/).

```
jQuery.altAlert = function (options)  
{  
    var defaults = {  
        title: "Alert",  
        buttons: {  
            "Ok": function()  
            {  
                jQuery(this).dialog("close");  
            }  
        }  
    };  

    jQuery.extend(defaults, options);  

    delete defaults.autoOpen;  

    window.alert = function ()  
    {  
        jQuery("<div />", {
            html: arguments[0].replace(/\n/, "<br />")
        }).dialog(defaults);  
    };  
};
```

**#85.** To convert a floating point number to an integer, you can use one of the following cryptic hacks (please don't):

```
3.14 >> 0 (via [2.9999999999999999 >> .5?](https://stackoverflow.com/questions/173070/29999999999999999-5))
3.14 | 0 (via [What is the best method to convert floating point to an integer in JavaScript?](https://stackoverflow.com/questions/131406/what-is-the-best-method-to-convert-to-an-integer-in-javascript))
3.14 & -1
3.14 ^ 0
~~3.14
```

Basically, applying any binary operation on the float that won't change the final value (i.e. identity function) ends up converting the float to an integer.

**#86.** You can redefine large parts of the runtime environment on the fly, such as [modifying the `Array` constructor](http://directwebremoting.org/blog/joe/2007/03/05/json_is_not_as_safe_as_people_think_it_is.html) or defining undefined. Not that you should, but it can be a powerful feature.

A somewhat less dangerous form of this is the addition of helper methods to existing objects. You can [make IE6 "natively" support indexOf on arrays](http://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Array/indexOf#Compatibility), for example.

**#87.** [JavaScript tips](http://code.google.com/p/jslibs/wiki/JavascriptTips) or the [jslibs project](http://code.google.com/p/jslibs/).

**#88.** You can make "classes" that have private (inaccessible outside the "class" definition) static and non-static members, in addition to public members, using closures.

Note that there are two types of public members in the code below. Instance-specific (defined in the constructor) that have access to private instance members, and shared members (defined in the `prototype` object) that only have access to private static members.

```
var MyClass = (function () {
    // private static
    var nextId = 1;

    // constructor
    var cls = function () {
        // private
        var id = nextId++;
        var name = 'Unknown';

        // public (this instance only)
        this.get_id = function () { return id; };

        this.get_name = function () { return name; };
        this.set_name = function (value) {
            if (typeof value != 'string')
                throw 'Name must be a string';
            if (value.length < 2 || value.length > 20)
                throw 'Name must be 2-20 characters long.';
            name = value;
        };
    };

    // public static
    cls.get_nextId = function () {
        return nextId;
    };

    // public (shared across instances)
    cls.prototype = {
        announce: function () {
            alert('Hi there! My id is ' + this.get_id() + ' and my name is "' + this.get_name() + '"!\r\n' +
                  'The next fellow\'s id will be ' + MyClass.get_nextId() + '!');
        }
    };

    return cls;
})();
```

To test this code:

```
var mc1 = new MyClass();
mc1.set_name('Bob');

var mc2 = new MyClass();
mc2.set_name('Anne');

mc1.announce();
mc2.announce();
```

If you have Firebug you'll find that there is no way to get access to the private members other than to set a breakpoint inside the closure that defines them.

This pattern is very useful when defining classes that need strict validation on values, and complete control of state changes.

To extend this class, you would put `MyClass.call(this);` at the top of the constructor in the extending class. You would also need to **copy** the `MyClass.prototype` object (don't reuse it, as you would change the members of `MyClass` as well.

If you were to replace the `announce` method, you would call `MyClass.announce` from it like so: `MyClass.prototype.announce.call(this);`

**#89.** The coalescing operator is very cool and makes for some clean, concise code, especially when you chain it together: `a || b || c || "default";` The gotcha is that since it works by evaluating to bool rather than null, if values that evaluate to false are valid, they'll often times get over looked. Not to worry, in these cases just revert to the good old ternary operator.

I often see code that has given up and used global instead of static variables, so here's how (in an example of what I suppose you could call a generic singleton factory):

```
var getInstance = function(objectName) {
  if ( !getInstance.instances ) {
    getInstance.instances = {};
  }

  if ( !getInstance.instances[objectName] ) {
    getInstance.instances[objectName] = new window[objectName];
  }

  return getInstance.instances[objectName];
};
```

Also, note the `new window[objectName];` which was the key to generically instantiating objects by name. I just figured that out 2 months ago.

In the same spirit, when working with the DOM, I often bury functioning parameters and/or flags into DOM nodes when I first initialize whatever functionality I'm adding. I'll add an example if someone squawks.

Surprisingly, no one on the first page has mentioned `hasOwnProperty`, which is a shame. When using `in` for iteration, it's good, defensive programming to use the `hasOwnProperty` method on the container being iterated over to make sure that the member names being used are the ones that you expect.

```
var x = [1,2,3];
for ( i in x ) {
    if ( !x.hasOwnProperty(i) )  { continue; }
    console.log(i, x[i]);
}
```

[Read here](http://ajaxian.com/archives/fun-with-browsers-for-in-loop) for more on this.

Lastly, `with` is almost always a bad idea.

**#90.** Using **Function.apply** to specify the object that the function will work on:

Suppose you have the class

```
function myClass(){
 this.fun = function(){
   do something;
 };
}
```

if later you do:

```
var a = new myClass();
var b = new myClass();
```

`myClass.fun.apply(b); //this will be like b.fun();`

You can even specify an array of call parameters as a secondo argument

look this: [https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Function/apply](https://developer.mozilla.org/en/Core_JavaScript_1.5_Reference/Global_Objects/Function/apply)

**#91.** Here's a simple way of thinking about 'this'. 'This' inside a function will refer to future object instances of the function, usually created with operator new. So clearly 'this' of an inner function will never refer to an instance of an outer function.

The above should keep one out of trouble. But there are more complicated things you can do with 'this.'

Example 1:

```
function DriveIn()
{
		this.car = 'Honda';
		alert(this.food);  //'food' is the attribute of a future object 
											 //and DriveIn does not define it.
}
 var A = {food:'chili', q:DriveIn};  //create object A whose q attribute 
																	 //is the function DriveIn;
 alert(A.car); //displays 'undefined' 
A.q();        //displays 'chili' but also defines this.car.
alert(A.car); //displays 'Honda' 
```

The Rule of This:

Whenever a function is called as the attribute of an object, any occurrence of 'this' inside the function (but outside any inner functions) refers to the object.

We need to make clear that "The Rule of This" applies even when operator new is used. Behind the scenes new attaches 'this' to the object through the object's constructor attribute.

Example 2:

```
function Insect ()
{
     this.bug = "bee";
     this.bugFood = function()
     {
         alert("nectar");
     }
 }

var B = new Insect();
alert(B.constructor); //displays "Insect"; By "The Rule of This" any
                      //ocurrence of 'this' inside Insect now refers 
                      //to B.    
```

To make this even clearer, we can create an Insect instance without using operator new.

Example 3:   

```
var C = {constructor:Insect};  //Assign the constructor attribute of C, 
                               //the value Insect.
C.constructor();               //Call Insect through the attribute. 
                               //C is now an Insect instance as though it 
                               //were created with operator new. [*]
alert(C.bug);                  //Displays "bee." 
C.bugFood();                   //Displays "nectar." 
```

The only actual difference I can discern is that in example 3, 'constructor' is an enumerable attribute. When operator new is used 'constructor' becomes an attribute but is not enumerable. An attribute is enumerable if the for-in operation "for(var name in object)" returns the name of the attribute.

**#92.** You can bind a JavaScript object as a HTML element attribute.

```
<div id="jsTest">Klick Me</div>
<script type="text/javascript">
    var someVariable = 'I was klicked';
    var divElement = document.getElementById('jsTest');
    // binding function/object or anything as attribute
    divElement.controller = function() { someVariable += '*'; alert('You can change instance data:\n' + someVariable ); };
    var onclickFunct = new Function( 'this.controller();' ); // Works in Firefox and Internet Explorer.
    divElement.onclick = onclickFunct;
</script>
```

**#93.** My first submission is not so much a hidden feature as a rarely used application of the property re-definition feature. Because you can redefine an object's methods, you can cache the result of a method call, which is useful if the calculation is expensive and you want lazy evaluation. This gives the simplest form of [memoization](http://en.wikipedia.org/wiki/Memoization).

```
function Circle(r) {
    this.setR(r);
}

Circle.prototype = {
  recalcArea: function() {
        this.area=function() {
            area = this.r * this.r * Math.PI;
            this.area = function() {return area;}
            return area;
        }
    },
  setR: function (r) {
      this.r = r;
      this.invalidateR();
    },
  invalidateR: function() {
        this.recalcArea();
    }
}
```

Refactor the code that caches the result into a method and you get:

```
Object.prototype.cacheResult = function(name, _get) {
  this[name] = function() {
    var result = _get.apply(this, arguments);
    this[name] = function() {
      return result;
    }
    return result;
  };
};

function Circle(r) {
    this.setR(r);
}

Circle.prototype = {
  recalcArea: function() {
        this.cacheResult('area', function() { return this.r * this.r * Math.PI; });
    },
  setR: function (r) {
      this.r = r;
      this.invalidateR();
    },
  invalidateR: function() {
        this.recalcArea();
    }
}
```

If you want a memoized function, you can have that instead. Property re-definition isn't involved.

```
Object.prototype.memoize = function(name, implementation) {
    this[name] = function() {
        var argStr = Array.toString.call(arguments);
        if (typeof(this[name].memo[argStr]) == 'undefined') {
            this[name].memo[argStr] = implementation.apply(this, arguments);
        }
        return this[name].memo[argStr];
    }
};
```

Note that this relies on the standard array toString conversion and often won't work properly. Fixing it is left as an exercise for the reader.

My second submission is getters and setters. I'm surprised they haven't been mentioned yet. Because the official standard differs from the de facto standard (defineProperty vs. **define[GS]etter**) and Internet Explorer barely supports the official standard, they aren't generally useful. Maybe that's why they weren't mentioned. Note that you can combine getters and result caching rather nicely:

```
Object.prototype.defineCacher = function(name, _get) {
    this.__defineGetter__(name, function() {
        var result = _get.call(this);
        this.__defineGetter__(name, function() { return result; });
        return result;
    })
};

function Circle(r) {
    this.r = r;
}

Circle.prototype = {
  invalidateR: function() {
        this.recalcArea();
    },
  recalcArea: function() {
        this.defineCacher('area', function() {return this.r * this.r * Math.PI; });
    },
  get r() { return this._r; }
  set r(r) { this._r = r; this.invalidateR(); }
}

var unit = new Circle(1);
unit.area;
```

Efficiently combining getters, setters and result caching is a little messier because you have to prevent the invalidation or do without automatic invalidation on set, which is what the following example does. It's mostly an issue if changing one property will invalidate multiple others (imagine there's a "diameter" property in these examples).

```
Object.prototype.defineRecalcer = function(name, _get) {
  var recalcFunc;
  this[recalcFunc='recalc'+name.toCapitalized()] = function() {
    this.defineCacher(name, _get);
  };
  this[recalcFunc]();
  this.__defineSetter__(name, function(value) {
      _set.call(this, value);
      this.__defineGetter__(name, function() {return value; });
  });
};

function Circle(r) {
    this.defineRecalcer('area',
             function() {return this.r * this.r * Math.PI;},
             function(area) {this._r = Math.sqrt(area / Math.PI);},
    );
    this.r = r;
}

Circle.prototype = {
  invalidateR: function() {
        this.recalcArea();
    },
  get r() { return this._r; }
  set r(r) { this._r = r; this.invalidateR(); }
}
```

**#94.** function can have methods.

I use this pattern of AJAX form submissions.

```
var fn = (function() {
        var ready = true;
        function fnX() {
            ready = false;
            // AJAX return function
            function Success() {
                ready = true;
            }
            Success();
            return "this is a test";
        }

        fnX.IsReady = function() {
            return ready;
        }
        return fnX;
    })();

    if (fn.IsReady()) {
        fn();
    }
```

**#95.** Simple self-contained function return value caching:

```
function isRunningLocally(){
    var runningLocally = ....; // Might be an expensive check, check whatever needs to be checked.

    return (isRunningLocally = function(){
        return runningLocally;
    })();
},
```

The expensive part is only performed on the first call, and after that all the function does is return this value. Of course this is only useful for functions that will always return the same thing.

**#96.** Closures:

```
function f() { 
    var a; 
    function closureGet(){ return a; }
    function closureSet(val){ a=val;}
    return [closureGet,closureSet];
}
```

[closureGet,closureSet]=f(); 
closureSet(5);
alert(closureGet()); // gives 5

closureSet(15);
alert(closureGet()); // gives 15

The closure thing here is not the so-called destructuring assignment (`[c,d] = [1,3]` is equivalent to `c=1; d=3;`) but the fact that the occurences of `a` in closureGet and closureSet still refer to the same variable. Even after closureSet has assigned `a` a new value!

**#97.** When you are write callbacks you have a lot of code, which will look like this:

```
callback: function(){
  stuff(arg1,arg2);
}
```

You can use the function below, to make it somewhat cleaner.

`callback: _(stuff, arg1, arg2) `

It uses a less well known function of the Function object of javascript, apply.

It also shows another character you can use as functionname: _.

```
function _(){
        var func;
        var args = new Array();
        for(var i = 0; i < arguments.length; i++){
                if( i == 0){
                        func = arguments[i];
                } else {
                        args.push(arguments[i]);
                }
        }
        return function(){
                return func.apply(func, args);
        }
}
```