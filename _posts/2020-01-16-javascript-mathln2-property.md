---
image: "/assets/default-social-image.png"
title: JavaScript Math.LN2 property
categories: JavaScript-math
---

In JavaScript, the Math.LN2 is a property that is generally used to calculate the value of a natural log of the 2. Natural log is of base e, defined as ln. So, its natural log of 2 is described as ln(2), the value of which is about 0.693.

**Difference between property and function in JavaScript**

JavaScript property is nothing but a value while method is a function which can be illustrated with the help of a situation as described below.

```
<script> 
  
// car is an object. 
var car = {}; 
  
// car.name is a property of the given object. 
car.name = "Audi", 
  
    // car.sayModel is a function of the given object. 
    car.sayModel = function() { 
        document.write("A8 <br>"); 
    } 
                  
    // printing property value. 
    document.write(car.name + '<br>'); 
                  
car.sayModel();        
</script> 
```

Output:

```
Audi
A8 
```

Here as we can see the object car's property, the string will be stored as "Audi" and accessible by car.name.

sayModel is a method i.e. an object function and can be obtained by using car.sayModel().

It can be noted that sayModel is merely a function that uses ().

**Syntax:**

`Math.LN2;`

**Parameters:**

Nothing is passed as a parameter here, since Math. LN2 is not a function but a property.

**Return Values:**

It simply returns the Natural log value of 2.

Example:

```
Input  : Math.LN2
Output : 0.6931471805599453
```

**Explanation:**

Just the natural log value of 2 i.e. Math. LN2 is displayed as output.

Example 1:

```
<script> 
  // Here value of Math.LN2 is printed. 
  document.write(Math.LN2);                       
</script> 
```

Output:

`0.6931471805599453`

Example 2:

Natural log value of 2 can be displayed as in function form as shown below.

```
<script> 
  // function is being called. 
  function get_Value_of_natural_log_of_2() 
  { 
     return Math.LN2; 
  } 
  
  // Calling Function. 
  document.write(get_Value_of_natural_log_of_2()); 
</script> 
```

Output:

`0.6931471805599453`

Example 3:

Here we assume Math.LN2 as a function, but in fact it is a property which is why the error is shown in output.

```
<script> 
  // Here we consider Math.LN2 as a  
  //function but in actual it 
  // is a property that is why error as 
  // output is being shown. 
  document.write(Math.LN2(12));         
</script> 
```

Output:

`Error: Math.LN2 is not a function`

Note: Search for errors in the console

**Supported Browsers:**

* Google Chrome
* Internet Explorer
* Firefox
* Opera
* Safari