---
image: "/assets/default-social-image.png"
title: JavaScript History object
categories: JavaScript-objects
---

The object window.history includes the history in the browser. First of all, window component can be deleted from window.history just by operating alone with the history object. The object in JS history includes a list of URLs that the user encounters. You may load previous, next in line or any other page using different methods by using the history object.

**Property of JavaScript history object :**

Length: returns the length of the session history URLs accessed by the user.

**Methods of JavaScript history object :**

forward(): The next page is loaded. Provides the same impact for the browser's click back too.
back(): The previous page is loaded. Provides the same impact as the browser's click forward.
go(): Loads the page number defined in the browser. History.go(distance) function has the same impact as clicking the browser's back or forward button and choosing the page you want to display exactly.

**To show the working of history.back() function:**

**Code #1:**

```
<html> 
<head> 
<title>MyPage back() example</title> 
</head> 
<body> 
<b>Press the back button</b> 
<input type="button" value="Back" onclick="previousPage()"> 
<script> 
function previousPage() { 
    window.history.back(); 
} 
</script> 
</body> 
</html>  
```

Output:

`Press the back button **Back**`

**To show the working of history.forward() function:**

**Code #2 :**

```
<html> 
<head> 
<title>MyPage forward() example</title> 
</head> 
<body> 
<b>Press the forward button</b> 
<input type="button" value="Forward" onclick="NextPage()"> 
<script> 
function NextPage() { 
    window.history.forward() 
} 
</script> 
</body> 
</html> 
```

Output:

`Press the forward button **Forward**`

**To show the working of history.go() function:**

Go(4) has the same consequence as clicking the forward button four times. A negative result in browser.go(-4) in the history has the same consequence as clicking the back button four times.

**Code #3:**

```
<html> 
<head> 
<title>MyPage go() example</title> 
</head> 
<body> 
<input type="button" value="go" onclick="NextPage()"> 
<script> 
function NextPage() { 
    window.history.go(4); 
} 
</script> 
</body> 
</html>  
```