---
title: Popular CSS Interview Questions And Answers
image: "/assets/default-social-image.png"
categories: CSS
---

**List of Most Popular CSS Interview Questions with Answers:**

Examples will explain the CSS Questions covering nearly all basic and advanced CSS categories.

CSS is one of Web development's most essential features. It is a language in which the presence of web pages can be represented.

Therefore, covering all the basic and advanced parts of the CSS is important. You need to know CSS to become a good web designer and easily break the web developer interview.

For your easy understanding, the list of the most frequently asked CSS interview questions and answers is given below.

Let's Begin!!

**Q #1) What is CSS?**

CSS outlines the style of an HTML webpage, it's a language in which we can set an HTML webpage's behavior. This explains how to view the HTML data on the computer.

CSS controls multiple HTML web pages layout. CSS is known as the Cascading Style Sheet.

**Name all the modules which are used in the current version of CSS.**

* Selectors
* Box Model
* Backgrounds and Borders
* Text Effects
* 2D/3D Transformations
* Animations
* Multiple Column Layout
* User Interface.

**Distinguish between CSS2 and CSS3.**

* CSS3 is split into two different sections, called a module. Whereas in CSS2, with all the data in it, it accesses a single document.
* On almost any platform, CSS3 modules are allowed and on the other side, CSS and CSS2 modules are not available in any browser.
* Within CSS3 we can note that many characteristics relevant to graphics such as Border-radius or box-shadow, flexbox, have been added.
* In CSS3, a user can use properties such as background-image, background-position and background-repeat styles for correct different background images on a website.

**Cite different types of CSS.**

* External – These are written in files that are separate.
* Internal – These are listed at the top of the code file on the web page.
* Inline – These are written directly next to the text.

**Why is the external style sheet useful?**

External style sheet is very convenient because we write all the styling codes in a single file and can be used anywhere by simply referring to the external style sheet file reference.

So if we make any changes to that external file, the changes can be seen on the webpage as well. So we can claim it's very helpful and while operating on bigger files it keeps the job simple.

**What are the uses of an embedded style sheet?**

In an HTML file, the embedded style sheet allows us the luxury of specifying styles within one place.

Using an embedded style sheet to use on multiple tag types of a web page, we can generate multiple classes and there is also no extra download needed to import the information.

Example:

```
<!DOCTYPE html>
<html>

<head>
<style type="text/css">
p {
  font-family: georgia, serif;
  font-size: x-large;
  color:#ff9900;
  }
a:hover {
  color: LimeGreen;
  text-decoration: none;
  }
</style>
</head>

<body>
<p>In an HTML file, the embedded style sheet allows us the luxury of specifying styles within one place. Using an embedded style sheet to use on multiple tag types of a web page, we can generate multiple classes and there is also no extra download needed to import the information.
</p>
</body> 

</html>
```

**How to use CSS selector?**

Using the CSS selector, we can pick the element we want to style so we can say it's a link between the style sheet and the HTML files.

CSS selector syntax is "select" HTML items that have been generated on their Id, class, type etc.

**Explain the concept of Tweening.**

Tweening is the method in which we create intermediate frames between two images so that the first image emerges into the second image.

It is used mostly to generate animation.

**Define CSS image scripts.**

CSS image scripts are a collection of images embedded in a single image.

By projecting multiple images into a single web page, this decreases the load time and query number to the server.

**Explain the term Responsive web design.**

It is a process in which we design and create a web page based on user behaviors and requirements based on various components such as screen size, web page portability on the various devices, etc.

It is therefore achieved using multiple dynamic layouts and grids.

**What are CSS counters?**

CSS counters are variables that can be improved by CSS laws which measure the number of times the variable was used.

**What is CSS specificity?**

The specificity of CSS is a rating or rank that specifies which declaration of style to use for an element

This universal selector has low specificity although ID selectors have high specificity.

In CSS, there are four categories that authorized the selector's specificity level.

* Inline style
* IDs
* Classes, Attributes, and pseudo-classes.
* Elements and pseudo-elements.

**How can we calculate specificity?**

We must begin with 0 to determine the specificity, then add 1000 for each ID and add 10 to the attributes, classes or pseudo-classes with each element name or pseudo-element and add 1 to them later.

As Example:

```
h2
             #content h2
            <div id=”content”>
              <h2 style=”color:#FF0000”>heading</h2>
            </div>
```

**How do we make a rounded corner by using CSS?**

Use the "border-radius" property to create a rounded edge. This property can be extended to any element.

Ex:

```
<html>
<head>

<style>
#rcorners1 {
    border-radius: 25px;
    background: #715751;
    padding: 20px;
    width: 200px;
    height: 150px;   
}

</style>
</head>

<body>
<h1>The border-radius Property</h1>
<p>Rounded corners for an element with a specified background color:</p>
<p id="rcorners1">Rounded corners!</p>
</body>

</html>
```

**How will you add border images to an HTML element?**

By using the CSS "border-image" attribute, we may set the image to be used as the border image next to an element.

Example:

```
#borderimg {
    border: 15px solid transparent;
    padding: 20px;
    border-image: url(border.png) 30 round;
}
```

**What are gradients in CSS?**

It is a CSS attribute that helps you to view a seamless transition between two or more colors.

Linear and Radial Gradient are two types of gradients in CSS.

**What is CSS flexbox?**

It enables you to design a flexible, responsive layout structure without using any CSS float or positioning property. Originally, you need to identify a flex container to use the CSS flexbox.

Example:

```
<!DOCTYPE html>
<html>
<head>

<style>
.flex-container {
  display: flex;
  background-color: #f4b042;
}

.flex-container > div {
  background-color: #d60a33;
  margin: 10px;
  padding: 20px;
  font-size: 30px;
}

</style>
</head>

<body>
<div class="flex-container">
  <div>1</div>
  <div>2</div>
  <div>3</div> 
</div>
<p> Example of  <em>flex</em>box.</p>
</body>
</html>
```

**Write all the properties of the flexbox.**

In the HTML website, flexbox properties used are flex-direction, flex-wrap, flex-flow, justify-content, align-items, align-content etc.

**How to align image vertically in a division that spans vertically on the whole webpage?**

Using the syntax verticle-align: middle in the `<div1>` element can be achieved, and even we can connect the two text spans with another span and after that we have to use verticle-align: middle in the #icon data.

**What is the difference between padding and margin?**

The margin in CSS is the property which helps us to create space around elements Even to the externally defined borders, we may create space.

In CSS we have properties of margin as: margin-top, margin-right, margin-bottom and Margin-left.

The property of Margin has certain specified values by using the following properties:

Auto – The margin is determined by the browser.
Length – this sets the magnitude of margin in px, pt, cm etc.
% – It sets the percentage of width in the element.
Inherit – with this we can inherit the property of margin from the parent element.

In CSS, padding is the property that helps us to create space around the content of an element as well as within some specified border

CSS padding also has properties such as:

Padding-top, Padding-right, Padding-bottom, Padding-left

Negative values are ineffective in padding.

```
div {
padding-top: 50px;
padding-right: 30px;
padding-bottom: 60px;
padding-left: 50px;
}
```

**What is the use of the Box Model in CSS?**

Answer: In CSS, the box model is a box that binds all the HTML elements and it includes features like margins, border, padding, and the actual content.

By using a box model we will get the authority to add the borders all around the elements and we can also define the space between the elements.

Q #22) How can we add icons to the web page?

Answer: We can add icons to the HTML webpage by using an icon library like font-awesome.

We have to add the name of the given icon class to any inline HTML element. (<i> or <span>) . Icons in the icon libraries are scalable vectors that can be customized with CSS.

Q #23) What is a CSS pseudo-class?

Answer: It is a class that is used to define a special state of an HTML element.

This class can be used by styling an element when a user snooped over it and also it can style an HTML element when it gets the focus.

selector:pseudo-class {
property:value;
}
Q #24) Explain the concept of pseudo-elements in CSS.

Answer: It is a feature of CSS which is used to style the given parts of an element.

For Example, we can style the first letter or line of an HTML element.

selector::pseudo-element {
property:value;
}
Q #25) What is CSS opacity?

Answer: It is the property that elaborates on the transparency of an element.

By this property, we can transparent the image that can take the values from 0.0-1.0, if the value is lower then the image is more transparent. IE8 and earlier versions of the browser can take the values from 0-100.

img {
opacity: 0.6;
filter: alpha(opacity=60); /* For IE8 and earlier */}
Q #26) Write all the position states used in CSS.

Answer: In CSS, there are four position states as stated below:

Static(default)
Relative
Fixed
absolute
Q #27) What are navigation bars in CSS?

Answer: By using navigation bars we can make an ordinary HTML page into a user-specific and more dynamic web page.

Basically, it is a list of links, hence use of <ul> and <li> elements makes the perfect sense.

ul {
list-style-type: none;
margin: 0;
padding: 0;
}
Q #28) What are the differences between relative and absolute in CSS?

Answer: The main difference between relative and absolute is that “relative” is used for the same tag in CSS and it means that if we write the left:10px then the padding will shift to 10px in the left while absolute is totally relative to the non-static parent.

It means if we write left:10px then the result will be 10px far from the left edge of the parent element.

Q #29) Define ‘important’ declarations used in CSS.

Answer: Important declarations are defined as that declaration which is having more importance than the normal declaration.

While executing, these declarations override the declaration which is having less importance.

For example, if there are two users Having an important declaration then one of the declarations will override the declaration of another user.

For Example:

Body {background: #FF00FF !important; color: blue}

In this body background has more weight than the color.

Q #30) Define different cascading methods that can be used inside the cascading order.

Answer: Cascading order is itself a sorting method that allows many other different sorting methods:

#1) Sort by origin: There are some rules which can provide the alternate way which can be defined as:

The normal weight of the style sheet of a particular provider will be overridden by the increased weight of the user's style sheet.
Stylesheet rules of a particular user will be overridden by the normal width of the provider’s style sheet.
#2) Sort by selector's specificity: Less specific selector is been overridden by the more specific selector.

For example, A Contextual selector is less specific in comparison to the ID selector which is a more specific one and with that contextual selector is been overridden by the ID selector.

#3) Sort by order specified: This comes in the scenario when the two selectors are the same in weight and the other properties than the specification which will be seen for overriding.

Example:

All other styles will be seen overridden if the style attribute is used for inline style.

And also if the link element is used for external style, then it will override the imported style.

Q #31) Differentiate between inline and block element.

Answer: Inline element does not have an element to set width and height and also it does not have the line break.

Example: em, strong, etc.

Block element specification:

They do have the line break.
They define the width by setting a container and also allow setting height.
It can also contain an element that occurs in the inline element.
Example:

width and height
max-width and max-height
min-width and min-height
hi (i=1-6)- heading element
p- Paragraph element.

Q #32) How is the concept of inheritance applied in CSS?

Answer: Inheritance is a concept in which the child class will inherit the properties of its parent class.

It is a concept which is been used in many languages and is the easy way of defining the same property again.

It is used in CSS to define the hierarchy from the top level to the bottom level. Inherited properties can be overridden by the children's class if the child uses the same name.

Example:

Body {font-size: 15pt;}

And another definition is being defined in the child class

Body {font-size: 15pt;}
H1 {font-size: 18pt;}

All the paragraph text will be displayed using the property and will be defined in the body except for the H1 style which will show the text in font 18 only.

Q #33) Differentiate between the ID and class.

Answer: Both id and class is been used in HTML and assigns the value from CSS.

Please find below the differences:

The ID is a kind of element which uniquely assigns a name to a particular element whereas class has an element with a certain set of properties that can be used for the complete block.
The id can be used as an element because it can uniquely identify it whereas class is also defined to block the elements and applies too many tags wherever it is used.
Id provides the restriction to use its properties to one specific element whereas in class the inheritance is applied to a specific block or group of the element.
Conclusion
This interview question and answer list will help you to crack the Web developer interview for fresher as well as experience level. These are the frequent questions asked in the interview.

Hope this article will help to crack and face any interview related to CSS for a Web developer.

We wish you all the success!!

Recommended Reading
9 Most Popular CSS Editors for Windows and Mac
How to Use CSS Selector for Identifying Web Elements for Selenium Scripts – Selenium Tutorial #6
Top 30+ Popular CSS Interview Questions and Answers