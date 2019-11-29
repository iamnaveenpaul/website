---
title: Top JavaScript Interview Questions & Answers
image: "/assets/default-social-image.png"
categories: JavaScript
---

1. What is JavaScript?

JavaScript is both client and server side scripting that can be embedded into HTML pages and that web browsers comprehend. JavaScript is also a object oriented programming language.

2. List the differences between Java and JavaScript?

Java is a standard language for programming. JavaScript, on the other hand, is a written program which can be introduced to HTML pages. Those two languages are not inter-dependent at all and are intended for different purposes. Java is an object-oriented programming (OOPS) or a structured programming language such as C or C++ while JavaScript is a scripting language on the client side.

3. What are JavaScript Data Types?

Number
String
Boolean
Object
Undefined

4. What is the use of isNaN function?

If the statement is not a number then the function isNan yields true, otherwise it returns false if it is infact a number.

5. Which is faster between JavaScript and an ASP script?

JavaScript is faster than ASP. JavaScript is a language on the client side and therefore does not need the web server assistance to run. On the other side, ASP is a language on the server side and is therefore often slower than JavaScript. Javascript is also now a language on the server side (nodejs).

6. What is negative infinity?

A number that can be obtained by dividing any negative number by zero in JavaScript.

7. Is it possible to break JavaScript Code into several lines?

A backslash '\' at the end of the first line breaks it like in a string statement.

Example:

`document.write("This is \a program");`

And if you switch to a new line when not in a string declaration, javaScript would neglect this line break.

Example:

```
var x=1, y=2,
z=
x+y;
```

This code however is absolutely fine, but not recommended because it disrupts debugging.

8. Which company developed JavaScript?

Netscape.

9. What are undeclared and undefined variables?

Undeclared variables are those that do not occur and are not defined in a code. If the code tries to interpret an undeclared variable's value, there will be a runtime error.

Undefined variables are those which have been declared in the program but no value has been given. If the program attempts to read an undefined variable's value, it returns an undefined value.

10. Write the code for adding new elements dynamically?

```
<html> 
<head> 
<title>t1</title> 
<script type="text/javascript"> 
	function addNode() { var newP = document.createElement("p"); 
	var textNode = document.createTextNode(" This is a new text node"); 
	newP.appendChild(textNode); document.getElementById("firstP").appendChild(newP); } 
</script> </head> 
<body> <p id="firstP">firstP<p> </body> 
</html>
```

11. What are global variables? How are these variable declared and what are the associated problems with using them?

Global variables are those available throughout the code's length, that is, they don't have any scope. To declare a local variable or object, the var keyword is used. If the var keyword is excluded, it will declare a global variable.

The issues by using global variables are the mismatch between local and global variable names. Furthermore, debugging and analyzing the program which depends on global variables is challenging.

Example:

`// Declare a global globalVariable = "Test";`


12. What is a prompt box?

A box that provides the user with a text box to enter input. To enter the text or number, the label and box will be provided.

13. What is 'this' keyword in JavaScript?

'This' applies to the object it was called.

14. Explain the working of timers in JavaScript? Also explain if there are any drawbacks of using the timer?

Timers are used at a set time to execute a piece of code or to repeat the code at a given time interval. The setTimeout, setInterval and clearInterval functions is used for this purpose.

The setTimeout(function, delay) is used after the specified delay to begin a timer that calls a specific function. The setInterval(function, delay) is used in the said delay to repeatedly execute the given function and only stops if canceled. The clearInterval(id) function informs to pause the timer.

Timers are run within a single thread, enabling events wait for execution queuing up.

15. Which symbol is used for comments in Javascript?

```
// comments for Single line and

/* for Multi

Line

*/
```

16. What is the difference between ViewState and SessionState?

ViewState is specific to a page in a session.

SessionState is unique to user specific data that can be found across in the web application, across all pages.

17. What is === operator?

=== is called as a strict operator of equality that returns true only when both operands have the same value without any conversion in type as well.

18. Explain how can you submit a form using JavaScript?

By using:

`document.form[0].submit();`

19. Does JavaScript support automatic type conversion?

Yes, it is the frequently used by programmers.

20. How can the style/class of an element be changed?

By:

`document.getElementById("myText").style.fontSize = "20?;`

or

`document.getElementById("myText").className = "anyclass";`

21. Explain how to read and write a file using JavaScript?

By using either JavaScript extensions or a web page with Active X objects.

22. What are all the looping structures in JavaScript?

For
While
do-while loops

23. What is Variable typing in Javascript?

It is used to apply a number to a variable, and the same variable can be applied to a string as well.

Example

```
i = 10;
i = "string";
This is called variable typing.
```

24. How can you convert the string of any base to integer in JavaScript?

The parseInt() is used to convert numbers between bases. It takes its first parameter as the string to be converted, and the second parameter is the base number of the given string.

For 4F (of base 16) to integer, we do:

`parseInt ("4F", 16);`

25. Explain the difference between "==" and "==="?

"==" just examines for their value similarity in appearance but "===" is a more of a strict equality measure of the two variables which it returns false if either/both the value and type are different.

26. What would be the result of 3+2+"7"?

Because 3 and 2 would be integers here, simple Mathamatical operation would make them 5 but as 7 is a string in line, the interlinking process between 5 and 7 would yield 57.

27. Explain how to detect the operating system on the client machine?

By using the navigator.platform string (property).

28. What do mean by NULL in Javascript?

It represents nothingness or no value at all. It implies no object or null string, no valid boolean value, no number or no array object.

29. What is the function of delete operator?

To remove the property as well as its value.

Example

```
var student= {age:20, batch:"ABC"};
delete student.age;
```

30. What is an undefined value in JavaScript?

If a variable allocated in the code doesn't exist or otherwise if not assigned any value to it. It could also be of a value where its property doesn't exist.

31. What are all the types of Pop up boxes available in JavaScript?

Alert, Confirm and Prompt

32. What is the use of Void(0)?

It is usually used to call another method or property without refreshing the page and while calling, the parameter passed is "zero".

33. How can a page be forced to load another page in JavaScript?

```
<script language="JavaScript" type="text/javascript" >

<!-- location.href="http://newhost/newpath/newfile.html"; //--></script>
```

34. What is the data type of variables in JavaScript?

All variables are object data types in JavaScript.

35. What is the difference between an alert box and a confirmation box?

An alert box displays only one button (OK) whereas the confirmation box displays two buttons (OK and cancel).

36. What are escape characters?

Escape characters like Backslash (\)  is used to display special characters (single quotes, double quotes, apostrophes, ampersands etc) so that it shouldn't cause confusion to computer for using those as the tools instead of displaying them, so those characters are placed after backslash for them to display.

Example:

```
document.write "I m a "good" boy"
document.write "I m a \"good\" boy"
```

37. What are JavaScript Cookies?

Cookies are generated when the user visits any website and that website stores some data they need about the user, these are the Cookies, which are typically small test files that are saved on a computer browser. This could be descriptions of the user name and data about the shopping cart from previous visits, as an example.

38. Explain what is pop()method in JavaScript?

The pop() method is similar to the shift() method, but the difference is that the shift() method works at the beginning of the array while pop() approach always extracts and returns the last element of the specified array. Then the array on which the call made is modified.

Example:

```
var cloths = ["Shirt", "Pant", "TShirt"];
cloths.pop();
//Now cloth becomes Shirt,Pant
```

39. Whether JavaScript has concept level scope?

No, the variable declared inside the function has a scope within that function in JavaScript

40. Mention what is the disadvantage of using innerHTML in JavaScript?

The disadvantages are:

* To everywhere the content is replaced.
* "appending to innerHTML", etc don't work.
* The old content is replaced by html if we use +=like "innerHTML = innerHTML + 'html'", etc
* It is much slower as the entire content of innerHTML is re-parsed and will be build into elements.
* We can potentially insert valid and broken HTML in the document and break it as the innerHTML does not provide validation scope making the web page unstable.

41. What is break and continue statements?

Break exits altogeather from the current loop, but Continue proceeds with the next statement in the loop.


42. What are the two basic groups of dataypes in JavaScript?

They are Primitive and Reference types, where the former is a number or Boolean while the latter is string or date.0

43. How generic objects can be created?

`var I = new object();`

44. What is the use of type of operator?

Typeof is used to return a variable type string description.

45. Which keywords are used to handle exceptions?

Try, Catch and finally are used for exception handling:

```
Try{
	Code
}
Catch(exp){
	Code to throw an exception
}
Finally{
	Code runs either it finishes successfully or after catch
}
```

46. Which keyword is used to print the text in the screen?

To print "Welcome":

`document.write("Welcome")`

47. What is the use of blur function?

To remove the focus from the specified object.

48. What is variable typing?

It is used to assign a number, then assign a string to the same variable. Example:

```
i= 8;
i="john";
```

49. How to find operating system in the client machine using JavaScript?

The 'Navigator.appversion' is used.

50. What are the different types of errors in JavaScript?

There are three types of errors:

* Load time errors: Errors that arise while accessing a web page, such as incorrect syntax errors that dynamically trigger errors.
* Run time errors: Errors that exist in the HTML code due to misuse of the command or illogical operations like dividing by zero or trying access an area of memory which doesn't exist.
* Logical Errors: The errors that arise as a result of the bad logic of a function that has different operation like the use of code which is syntactically correct but that does not fulfills the required job as in case of an infinite loop.

51. What is the use of Push method in JavaScript?

The push method is used to add or append to the end of an array for one or more elements We may add multiple elements using this method by passing many arguments.

52. What is unshift method in JavaScript?

Unshift method is like a push method that operates at the start of the array. Use this method to prepend one or more elements to the array list.

53. What is the difference between JavaScript and Jscript?

JavaScript is developed by Netscape and Jscript by Microsoft and both of them are similar.

54. How are object properties assigned?

Properties are assigned to objects by-

`obj["class"] = 12;`

or

`obj.class = 12;`

55. What is the 'Strict' mode in JavaScript and how can it be enabled?

Strict Mode introduces some compulsions where JavaScript shows errors for a piece of codes that have not previously shown an error but may be troublesome and potentially unsafe under the strict mode. Strict mode often eliminates certain errors that inhibit the efficient operation of JavaScript engines.

Strict mode can be activated by adding the string above the file with the literal "use strict." For Example:

```
function myfunction() {
    "use strict";
    var v = "This is a strict mode function";
}
```

56. What is the way to get the status of a CheckBox?

alert(document.getElementById('checkbox1').checked);

This will return TRUE as alert if the CheckBox will be checked.

57. How can the OS of the client machine be detected?

By navigator.appVersion string 

58. Explain window.onload and onDocumentReady?

Until all the page data is loaded, the onload feature will not work. It adds to a significant delay before the script execution.

onDocumentReady loads the code directly after loading DOM which allows code to be manipulated early.

59. How will you explain closures in JavaScript? When are they used?

Closure is a locally assigned variable associated with a function which persists in memory when the function returns. For example:

```
function greet(message) {

    console.log(message);

}

function greeter(name, age) {

    return name + " says howdy!! He is " + age + " years old";

}

// Generate the message

var message = greeter("James", 23);

// Pass it explicitly to greet

greet(message);

This function can be better represented by using closures

function greeter(name, age) {

    var message = name + " says howdy!! He is " + age + " years old";

    return function greet() {

        console.log(message);

    };

}

// Generate the closure

var JamesGreeter = greeter("James", 23);

// Use the closure

JamesGreeter();
60. How can a value be appended to an array?

A value can be appended to an array in the given manner -

arr[arr.length] = value;
```

61. Explain the for-in loop?

The for-in loop is used to cycle through an object's property. For ex:

```
for (variable name in object){
	statement or block to execute
}
```

In each iteration, the variable name is associated with one property from the object and the process persists until all of the object's properties are exhausted.

62. Describe the properties of an anonymous function in JavaScript?

A function declared without a specified identifier. Also, it is inaccesible after its declaration.

```
var anon = function() {
	alert('I am anonymous');
};
anon();
```

63. What is the difference between .call() and .apply()?

With some little exception, the use of function .call() and .apply() are very similar, .call() is used when the programmer recognizes the number of the arguments of the function, as they must be mentioned in the call statement. whereas if the number is not known, .apply() is used. The function .apply() expects an array to be an argument.

The fundamental difference between .call() and .apply() is in passing arguments to the function. As an example:

```
var someObject = {
myProperty : 'Foo',

myMethod : function(prefix, postfix) {

	alert(prefix + this.myProperty + postfix);
}
};
someObject.myMethod('<', '>'); // alerts '<Foo>'
var someOtherObject  = {

	myProperty : 'Bar'

};
someObject.myMethod.call(someOtherObject, '<', '>'); // alerts '<Bar>'

someObject.myMethod.apply(someOtherObject, ['<', '>']); // alerts '<Bar>'
```

64. Define event bubbling?
	
JavaScript enables the nesting of DOM components within each other. In this case, if the child's handler is clicked, the parent's handler will also function as well as if it is clicked.

65. Is JavaScript case sensitive? Give an example?

Yes, For example, a function parseInt is not same as the Parseint function.

66. What boolean operators can be used in JavaScript?

In JavaScript, Boolean are the 'And' Operator `&&`, 'Or' Operator `||` and the 'Not' Operator `!`.

67. How can a particular frame be targeted, from a hyperlink, in JavaScript?

This can be achieved by using the attribute 'target ' to include the name of the necessary frame in the hyperlink.

`<a href="/newpage.htm" target="newframe">>New Page</a>`

68. What is the role of break and continue statements?

Break exits the current loop while Continue progresses with a new recurrence within the current loop.

69. Write the point of difference between web-garden and a web-farm?

Both are systems for web hosting. The only distinction is that web-garden is a configuration that involves multiple processors in one server while web-farm is a wider system and requires more than one server.

70. How are object properties assigned?

Assigning entity property is performed in the same manner as assigning a value to a variable For example, the action value of a form object is assigned as 'submit': 

```
Document.form.action="submit";
```

71. What is the method for reading and writing a file in JavaScript?

By Using JavaScript extensions that usually runs from JavaScript Editor:

`fh = fopen(getScriptPath(), 0);`

the above is used for opening a file.

72. How are DOM utilized in JavaScript?

DOM (Document Object Model) is responsible for the communication of different objects in a document. The design of web pages involves DOM, which contains objects such as paragraph links etc. Such objects can be used to perform behavior such as inserting or removing. For adding additional features to a web page, DOM is used. In addition, using the API provides a benefit over other existing models.

73. How are event handlers utilized in JavaScript?

Events are actions resulting from the user's activities, such as clicking a link or filling out a form. To control all these events properly, an event handler is needed. Event handlers are an optional entity feature for the object. The attribute contains the title of the event and the action taken when the event occurs.

74. Explain the role of deferred scripts in JavaScript?

By default, the HTML code parsing is halted during loading of the page until the script execution which ensures that if the server becomes slow or the script is particularly heavy, the web page will be shown with a delay Scripts delay the execution while using Deferred until the HTML parser runs. This reduces the time of loading of web pages and shows them quickly.

75. What are the various functional components in JavaScript?

First-class functions: JavaScript functions are used as objects of first class. This usually means that these functions can be passed to other functions as arguments, returned from other functions as values, assigned to variables, or stored in data structures as well.

Nested functions: The functions are called Nested functions, which are specified within other functions. They are called the main function is invoked every time.

76. What are Screen objects?

They are used to read the data from the client's screen and some of their properties are:

AvailHeight: Provides the height of client's screen
AvailWidth: Provides the width of client's screen.
ColorDepth: Provides the bit depth of images on the client's screen
Height: Provides the total height of the client's screen, including the taskbar
Width: Provides the total width of the client's screen, including the taskbar

77. Explain the unshift() method ?

Similar to the push(), the unshift() method is usable at array initialization

This method is functional at the starting of the array, unlike the push(). This applies to the top of an array which adds the required number of elements, like for ex:

```
var name = [ "john" ];
name.unshift( "charlie" );
name.unshift( "joseph", "Jane" );
console.log(name);
```

The output shown will be:

[" joseph "," Jane ", " charlie ", " john "]

78. Define unescape() and escape() functions?

The escape() feature is responsible for coding a sequence in order to transfer the data across a network from one system to the other.

For Example:

```
<script>
	document.write(escape("Hello? How are you!"));
</script>
```

Output: Hello%3F%20How%20are%20you%21

The unescape() function is very significant because it decodes the encrypted string.

For example:

```
<script>
	document.write(unescape("Hello%3F%20How%20are%20you%21"));
</script>
```

Output: Hello? How are you!

79. What are the decodeURI() and encodeURI()?

EncodeURl() is used to convert the URL into their hex code. And to convert the encoded, or hex coded URL here back to normal, DecodeURI() is used.

```
<script>
	var uri="my test.asp?name=ståle&car=saab";

	document.write(encodeURI(uri)+ "<br>");

	document.write(decodeURI(uri));
</script>
```

Output -

my%20test.asp?name=st%C3%A5le&car=saab

my test.asp?name=ståle&car=saab

80. What does the following statement declares?

`var myArray = [[[]]];`

That declares an array of three dimensional type.

81. How are JavaScript and ECMA Script related?

ECMA Script are sort of rules and guidelines, whereas Javascript is a web development scripting language.

82. What is namespacing in JavaScript and how is it used?

Namespacing is used under a unique name to group the desired functions, variables, etc. It is a name attached to the functions, objects and properties needed. It increases programming modularity which encourages reuse of the code.

83. How can JavaScript codes be hidden from old browsers that don't support JavaScript?

By adding  in the code, `<!--` after and `//-->` before the `<script>` tag.

This JavaScript script is now being viewed by old browsers as a long HTML post. While, a JavaScript supporting browser will accept the `<!--` and `//-->` statements as one-line.