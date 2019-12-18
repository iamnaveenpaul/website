---
title: JavaScript Location protocol Property
image: "/assets/default-social-image.png"
categories: JavaScript-basics
---

**What is Protocol?**

A network protocol for interaction between network devices specifies rules and conventions. Two machines can interact with each other by following these rules and can exchange information.

**Syntax:**

`location.protocol`

**Properties:**

* **ftp:** The File Transfer Protocol (FTP) is a standard network protocol used for the transmission of computer files between the client and the server on the network.
* **http:** The Hypertext Transfer Protocol (HTTP) is a distributed system application protocol.
* **https:** The Hypertext Transfer Protocol Secure (HTTPS) is an enhancement of the Hypertext Transfer Protocol (HTTP) for secure and is commonly used Internet communication.
* **file:** Used as a file or as a local server system.
* **mailto:** Used in system of mail.
* **return Value:** The property of the protocol returns the current URL protocol including the colon (:)

The location.protocol property in JavaScript is shown in the following example:

Example:

```
<!DOCTYPE html> 
<html> 
    <head> 
        <title>Location protocol property</title> 
        <style>
            #Mw { 
                position: center; 
                width: 220px; 
                height: 50px; 
                color: green; 
            } 
        </style> 
          
        <script> 
          
            // Function that tells the Protocol 
            // of current url. 
            function Protocol() { 
                var mw = location.protocol; 
                alert("protocol is: " + mw); 
            } 
        </script> 
    </head> 
    <body> 
        <div id = "Mw"> 
                <h1>This is my world</h1> 
        </div> 
        <p>Click to know the protocol of current URL.</p> 
        <button onclick = "Protocol()">Protocol</button> 
    </body> 
</html> 
```