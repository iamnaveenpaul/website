---
title: JavaScript basics
image: "/assets/default-social-image.png"
categories: JavaScript
---

JavaScript is a programming language that brings interactivity to your website (e.g. games, feedback by pressing buttons or inputting form information, interactive design, and animation). With this fun word, this article helps you get going and gives you an idea of what's possible.

**What is JavaScript, really?**

[JavaScript](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript) is a full-fledged [dynamic programming language](https://developer.mozilla.org/en-US/docs/Glossary/Dynamic_programming_language) that can provide dynamic interactivity on websites when applied to an HTML document. It was invented by the Mozilla project's co-founder Brendan Eich, the Mozilla Foundation, and the Mozilla Corporation.

JavaScript is incredibly flexible and welcoming for newcomers. You will build games interactive 2D and 3D graphics, comprehensive database-driven applications, and much more with more practice!

JavaScript is lightweight but very versatile in itself. Developers have created a large variety of tools in addition to the basic JavaScript code, opening with minimal effort a huge amount of extra functionality. These include the following:

* Browser Application Programming Interfaces [(APIs)](https://developer.mozilla.org/en-US/docs/Glossary/API) — Web browser built-in APIs that provide features such as dynamically designing HTML and defining CSS templates, capturing and editing a video stream from the webcam of the client, or producing 3D graphics and audio samples.
* Third-party APIs — Allow developers from other content providers, such as Twitter or Facebook, to incorporate functionality into their sites.
* Third-party frameworks and libraries — To enable you to quickly build sites and applications, you can apply these to your HTML.

Because this article should only be a light introduction to JavaScript, at this stage we will not confuse you by talking in detail about the difference between the core JavaScript language and the various tools listed above. You can learn all this later in detail, in our [learning area](https://developer.mozilla.org/en-US/docs/Learn/JavaScript) for JavaScript, and in the rest of MDN.

Below we'll introduce you to some core language aspects, and you'll also play with some features of the browser's API. Have a lot of fun!

**A "Hello world!" example**

The section above may sound really exciting, and so it should— JavaScript is one of today's most vibrant web technologies, and as you begin to make good use of it, your websites will enter a new dimension of power and creativity.

However, it's a little harder to become comfortable with JavaScript than getting comfortable with HTML and CSS. You may need to start small and continue to work in regular small steps. To begin with, we'll show you how to add some basic JavaScript to your page by creating an example of "Hello world!" which is also the norm for [basic programming examples](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program).

Importantly, If you have not followed this tutorial code including the rest of our course, [access this](https://github.com/mdn/beginner-html-site-styled/archive/gh-pages.zip) as an example and use it as a base point.

First, go to the test site and create a new folder called `scripts`. And create a new file called `main.js` in the new scripts folder you just made. Save it in your folder of `scripts`.

Next add the following element in your `index.html` file on a new line just before the `</body>` tag closes

`<script src="scripts/main.js"></script>`

It effectively does the same function as the CSS `<link>` feature — it adds the JavaScript to the page, so it can influence the HTML (along with the CSS and anything else on the site).

Now apply to the main.js directory the following code:

```
const myHeading = document.querySelector('h1');
myHeading.textContent = 'Hello world!';
```

Eventually, make sure you save the HTML and JavaScript documents, then load index.html in your browser.

Note that The reason we put the `<script>` component close to the bottom of the HTML document is because the user loads HTML in the order it occurs in the folder. If the JavaScript is first loaded and it is meant to impact the HTML below, it may not work as the JavaScript is enabled before the HTML on which it is supposed to work. Therefore, the best strategy is often to bring JavaScript close to the bottom of the HTML page.

What has happened?

Using JavaScript, your heading text has now been changed to "Hi world!." You achieved this by first using the `querySelector()` method to grab a link to your heading and place it in a variable called `myHeading`. This is very close to the use of CSS selectors which we did. If you want to do something about an object, you must first pick it.

You then set the value of the `textContent` property of the `myHeading` parameter (which reflects the heading content) to "Hello world!."

Note: Both of the features you used above are Document Object Model (DOM) API components that allow you to manipulate documents.

**Language basics crash course**

Let's clarify some of the JavaScript language's core features and give you a better idea of how everything operates. It's worth noting that these features are specific to all programming languages, so you're well on the path to being able to program just about anything if you learn these basics!

Important: Try entering the code lines in your JavaScript console in this article to see what's going on. See [Explore web developer tools](https://developer.mozilla.org/en-US/Learn/Discover_browser_developer_tools) for information on JavaScript consoles.

**Variables**

[Variables](https://developer.mozilla.org/en-US/docs/Glossary/Variable) are containers in which values can be placed. You start by declaring a variable with the `var` (less recommended, dive deeper to explain) or the `let` keyword, followed by any name you would like to call it:

`let myVariable;`

Note: A semicolon at the end of a line shows where a sentence ends; only when dividing sentences on a single line is absolutely necessary. Some individuals, though, believe that putting them in at the end of each sentence is a good practice. There are other rules for when to use them— see [Your JavaScript Semicolon Guide](http://news.codecademy.com/your-guide-to-semicolons-in-javascript/) for more specifics.

Note: Nearly anything you can call a variable but some naming limitations apply (see this page on [naming rules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_Types#Variables)). If you're unsure, your variable name can be [checked](https://mothereff.in/js-variables) to see if it's valid.

Note: JavaScript is sensitive to case — `myVariable` is a variable other than `myvariable`. Check the casing if you have problems with your code!

Note: watch out the difference between `var` and `let` for more information: [the difference between var and let](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables#The_difference_between_var_and_let).

You should assign it a value after a variable has been declared:

`myVariable = 'Bob';`

On the same row, you can do both of these operations if you want:

`let myVariable = 'Bob';`

By naming the variable by name you can extract the value:

`myVariable;`

You may later choose to adjust it after assigning a value to a variable:

```
let myVariable = 'Bob';
myVariable = 'Steve';
```

Note that variables may contain values of different types of data:

**Example of variable and explanation**

**String:**

A string is termed for a text sequence. You will include it in quote marks to show that the value is a string.

`let myVariable = 'Bob';`

**Number:**

Numbers are not accompanied by quotations.

`let myVariable = 10;`

**Boolean:**

True/False value. The terms `true` and `false` are specific JS keywords, and no quotations are required.

`let myVariable = true;`

**Array:**

A framework that allows several values to be contained in a single reference.

`let myVariable = [1,'Bob','Steve',10];`

Refer to each member of the array like this:

`myVariable[0]`, `myVariable[1]`, etc.

**Object:**

Ultimately, that's anything. In JavaScript, everything is an object that can be stored in a variable. Keep this in mind while you are learning.

`let myVariable = document.querySelector('h1');`

And all of the above examples too.

So why are we going to need variables? Okay, there is a need for variables in software to do anything fascinating. When values can not be modified, you can not do anything creative, such as customizing a welcome note or modifying the picture shown in an image gallery.

**Comments:**

Comments are, in fact, short text fragments that can be inserted to code that the browser avoids. Comments can be put in JavaScript code just as you can in CSS:

```
/*
Everything here in between is a comment.
*/
```

If your comment does not contain line breaks, putting it behind two slashes like this is often easier:

`// Whatever here is a comment`

**Operators:**

An [operator](https://developer.mozilla.org/en-US/docs/Glossary/operator) is a representation of math symbol that produces results dependent on two (or variables) values. Some of the easiest operators can be seen in the table below, along with some instances to seek in the JavaScript console.

**Operator explanation with symbols:**

**Addition:**

Used to combine two numbers or to combine two strings.

`6 + 9;`

`"Hello " + "world!";`

**Subtraction, Multiplication, Division:**

Through basic math, they do what you would want them to do.

`9 - 3;`

`8 * 2;` // multiplication in JS is an asterisk

`9 / 3;`

**Assignment:**

A variable is assigned a value as you've already seen this using `=`.

`let myVariable = 'Bob';`

**Equality:**

Does a check to see if two values are equivalent to each other using `===` and returns a verdict that is true/false (Boolean).

`let myVariable = 3;`

`myVariable === 4;`

**Not, Does-not-equal:**

Returns what it precedes, the logically opposite value; it transforms a `true` into a `false` etc. The negation operator checks that two values are not identical when used in combination with the Equality operator. Uses `!` and `!==`

The basic term for "Not" is true but the analogy is false because we negate it:

```
let myVariable = 3;
!(myVariable === 3);
```

"Does-not-equal" with different syntax gives basically the same result. This is where we test "is myVariable NOT equal to 3." It makes it false as myVariable is equivalent to 3:

```
let myVariable = 3;
myVariable !== 3;
```

There's a lot of operators to try, but for now that's enough. For a complete list, see [Expressions and Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators).

Note: While doing calculations, combining data types will lead to some strange results, so be sure to properly relate to your variables and get the results you anticipate. For example, enter your console with `"35" + "25"`. Why don't you get the expected result? Because the quote marks turn the numbers into strings, instead of adding numbers, you ended up concatenating strings. When you enter, you will get the right result for `35 + 25`.

**Conditionals**

Conditionals are code constructs that allow you to check whether an expression returns true or not by running alternate code disclosed by its result. A very common conditional form is `if... else` statement. For instance:

```
let iceCream = 'chocolate';
if(iceCream === 'chocolate') {
  alert('Yay, I love chocolate ice cream!');    
} else {
  alert('Awwww, but chocolate is my favorite...');    
}
```

The expression within the `if( ... )` is the test, this uses the identity operator (as described above) to compare the `iceCream` variable with the `chocolate` string to see whether the two are equal. If this analogy is `true`, the first code block will be implemented. If the correlation is not true it will miss the first block and instead run the second block of code after the `else` statement.

**Functions**

[Functions](https://developer.mozilla.org/en-US/docs/Glossary/Function) are a way you want to recycle package functionality. You should call a method with the name of the function instead of updating the entire code any time you need the process. For example, you've already seen some uses of the above functions:


`let myVariable = document.querySelector('h1');`

`alert('hello!');`


Both features, `document.querySelector` and `alert` are incorporated into the browser so you can use them whenever you want.


If you see something that looks like a name for a variable but has parentheses `()` after it, it's probably a function. Many functions take [arguments](https://developer.mozilla.org/en-US/docs/Glossary/Argument) that are bits of data that they need to do their job. Those go inside the parentheses, if there is more than one statement, separated by commas.

For example, the `alert()` function makes a pop-up box appear in the browser window, but to tell the function what to write in the pop-up box, we need to give it a string as an argument.

The good news is that you can describe your own functions — we write a simple function in this next instance which takes two numbers as arguments and multiplies them:

```
function multiply(num1,num2) {
  let result = num1 * num2;
  return result;
}
```

Try to run the above function in the console then evaluate it with multiple arguments. For example:

```
multiply(4, 7);
multiply(20, 20);
multiply(0.5, 3);
```

Note that the `return` statement tells the browser to exit the function to return the `result` variable so that it can be used. This is necessary because the variables defined within the functions can only be found within those functions. This is called the [scoping](https://developer.mozilla.org/en-US/docs/Glossary/Scope) variable, Read more on [this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Values,_variables,_and_literals#Variable_scope)

**Events**

Real website interactivity requires events. These are code structures that listen to browser stuff and run code in response. The most obvious example is the [click event](https://developer.mozilla.org/en-US/docs/Web/Events/click) that the browser fires when you click with your mouse on something. To prove this, enter the following in your console and click on the current webpage:

```
document.querySelector('html').onclick = function() {
    alert('Ouch! Stop poking me!');
}
```

An event can be attached to an element in many ways. Here we choose the `<html>` element, setting its `onclick` handler property to an anonymous function that contains the code that we want to run the click event.

Note that

`document.querySelector('html').onclick = function() {};`

is equivalent to

```
let myHTML = document.querySelector('html');
myHTML.onclick = function() {};
```

It is just simpler.

**Supercharging our example website**

Now we've gone through a few fundamentals of JavaScript, let's add some cool features to our page for instance to see what's possible.

**Adding an image changer**

In this section, using some more DOM API features, we will add an additional image to our site, using some JavaScript to switch between the two when clicking on the image.

1. First of all, consider another image on your page that you would like to feature. Make sure it's the same size as or as close as possible to the first image
2. 1. Save this image in your `images` folder and rename the image to firefox2.png.
3. Go to your `main.js` file and enter the JavaScript below. (If there's already your "Hello world!" JavaScript, remove it.)

```
let myImage = document.querySelector('img');

myImage.onclick = function() {
    let mySrc = myImage.getAttribute('src');
    if(mySrc === 'images/firefox-icon.png') {
      myImage.setAttribute ('src','images/firefox2.png');
    } else {
      myImage.setAttribute ('src','images/firefox-icon.png');
    }
}
```

4. Save all files in your browser and launch `index.html`. Now, when you click on the image the other image should be changed with original!

In the `myImage` variable you store a reference to your `<img>` element Next, you make the `onclick` event handler property of this variable equivalent to a anonymous function. Now, every time you click on this element:

1. You get the value of the `src` attribute of the image.
2. 1. To test if the `src` value is equal to the path to the original image, you use a conditional:
1. If this is the case, you adjust the `src` value to the 2nd image path causing the other image to be loaded within the element `<img>`.
2. 1. If not (meaning it must have changed already), the `src` value flips back to the original path of the image to the original state.

**Adding a personalized welcome message**

Next, when the user first navigates to the site, we will add another bit of code, changing the title of the page to a custom welcome message. If the user leaves the site and returns later, this welcome message will remain— we will save it using the [Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API). We will also include an option to change the user and, therefore, the welcome message whenever necessary.

In index.html, just before the `<script>` element, add the following line:

`<button>Change user</button>`

Insert the following code at the bottom of the file in `main.js`, written exactly. It corresponds to the new button and title, storing it within variables:

```
let myButton = document.querySelector('button');
let myHeading = document.querySelector('h1');
```

Now add the following feature to set the customized greeting where this will not do anything yet, but in a moment we'll correct it:

```
function setUserName() {
  let myName = prompt('Please enter your name.');
  localStorage.setItem('name', myName);
  myHeading.textContent = 'Mozilla is cool, ' + myName;
}
```

The function includes a feature `prompt()` which creates a dialog box, much like `alert()`. Nevertheless, this `prompt()` function asks the user to insert any data after the user clicks 'OK', storing it in a variable We request the client to type their name in this situation. Next, we call a `localStorage` API, which helps us to store and later retrieve data in the app. We use the feature `setItem()` of localStorage to build and store a data item called `'name'` and set its value to the attribute `myName` which contains the information entered by the client. Finally, we set a string to the `textContent` of the heading plus the recently saved name of the user.

Now, add this `if ... else` block, we might call it the initialization script, because when it initially loads, it constructs the app:

```
if(!localStorage.getItem('name')) {
  setUserName();
} else {
  let storedName = localStorage.getItem('name');
  myHeading.textContent = 'Mozilla is cool, ' + storedName;
}
```

First, this block uses the negation operator (logical NOT, expressed by !) to verify the presence of the `name` information. If not, the method `setUserName()` will be performed to construct it. If it exists (i.e. the user set it during a previous visit), we use `getItem()` function to retrieve the stored name and set the `textContent` of the heading to a string, plus the name of the user, as we did in `setUserName()`.

Lastly, put the event handler `onClick` on the button below. The `setUserName()` function is executed when pressed. This allows the user to set a new name by clicking on the button:

```
myButton.onclick = function() {
  setUserName();
}
```

Now it will ask you for your username when you first visit the site, then send you a personalized message. Whenever you like, you can change the name by clicking button. Because the name is saved within `localStorage` as an added bonus, it continues after the link is closed down, maintaining the custom message there when you open the web again at any time!

**A user name of null?**

Try to press the 'Cancel' button while running that instance and you get the dialog box which asks you to type the user name. You should end with the sentence "Mozilla is cool, null". This is because the value is set as `null` when you cancel the prompt, a special value in JavaScript which essentially refers to the absence of a value.

Also just try to press OK without inserting a name — you will end up with the title which says "Mozilla is cool,", which is quite evident.

When you prefer to avoid such issues, by modifying the `setUserName()` method to this, you might verify that the user did not enter `null` or an empty name:

```
function setUserName() {
  let myName = prompt('Please enter your name.');
  if(!myName || myName === null) {
    setUserName();
  } else {
    localStorage.setItem('name', myName);
    myHeading.innerHTML = 'Mozilla is cool, ' + myName;
  }
}
```

In layman's terms, if `myName` does not have any meaning or if its value is `null`, run `setUserName()` from the beginning.

**Conclusion**

If you followed all through out this post, you end up with a page which looks like [this](https://mdn.github.io/beginner-html-site-scripted/):

You can compare your work with [this](https://github.com/mdn/beginner-html-site-scripted/blob/gh-pages/scripts/main.js) completed example code on GitHub if you get stuck.

We barely touched JavaScript's vast existance. If you've enjoyed learning and want to make further progress, you can go [here](https://developer.mozilla.org/en-US/docs/Learn/JavaScript).