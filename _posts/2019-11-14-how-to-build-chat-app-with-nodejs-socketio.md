---
title: How to build chat app with Node.js & Socket.io
image: https://picsum.photos/2560/600?image=733
categories:
- Nodejs-socketio
---

It’s not an easy job to learn socket.io with node js at the same time, one reason to add is when someone who is trying to learn node js or is at an amateur level at it, he would be more likely interested in trying out all the features that the socket.io provide, also when someone is not familiar with the node.js, it’s protocol for WebSockets is left for himself to borrow it from random snippets of the code. 

On top of that, trying to parse its protocol while learning the socket.io library along with the basics of node js all at the same time becomes even more frustrating. I was shocked to see that there are no good quick tutorials on how to learn the basics of using socket.io with node js.


So I thought I would like to try to fill this void. Note that is updated to run on node 5.0.0 and socket 1.3.7 so I would recommend at least these versions for the code execution. We will cover the three steps in this tutorial. The first step is setting up a Node.js server and router, after this is connecting the socket.io to this server, and the final step is to send data to the client as well as server through that socket connection. 

Let’s begin..

# Your Basic Server:
We’ll use the http library module to initiate the server in Node.js, there are several kinds of modules we could apply and they all do the same job

```
var http = require('http');
var server = http.createServer();
server.listen(8001);
```

Now we have a server with these lines, but they don’t do any job as of now, you can save this as server.js and run node server.js, you will now see you command line process waiting for something to happen on the server. Let’s make the server work:

```
var http = require('http');
var server = http.createServer(function(request, response){
			response.writeHead(200, {'Content-Type': 'text/html'});
			response.write('hello world');
			response.end();
});
server.listen(8001);
```

Now we are sending some information to the client with the changes that we now made, nothing would happen still but if we go to http://localhost:8001, we will see a page that says “hello world”! after you save this server.js and run node server.js.

Each time whenever we load http://localhost:8001, the action is executed whatever we put inside the createServer. Let’s go step by step each line and go through what we did:


```
var server = http.createServer(function(request, response){});
server.listen(8001);
```

We have created the usual server but now we are passing a function that defines the request and response from server.
```
var server = http.createServer(function(request, response){
    //...
});
```
We simply say here that we are taking some action on every request and response done with the server
 ```
response.writeHead(200, {'Content-Type': 'text/html'});
```

We have writeHead that is written to the response header where here it describes the response and content type (that can be any common MIME types) for HTTPS code (you can also define any other elements found in the response header for HTTP), here what we simply done is define how client receiving data.
`response.write('hello world');`

Here ‘Write’ is response content “Hello world” and the server will bring the content to the served document, this line defines the response action that is being executed here.
  ` response.end();`
This final line shown here simply says that we have defined all the response and action and telling it to execute whatever code is written.

**Creating The Router:**
Now we have to add something to server.js because we have a server which can only serve our root domain:

```
   var http = require("http");
    var url = require('url');
    var fs = require('fs');
    var server = http.createServer(function(request, response){
        var path = url.parse(request.url).pathname;
        switch(path){
            case '/':
                response.writeHead(200, {'Content-Type': 'text/html'});
                response.write('hello world');
                response.end();
                break;
            case '/socket.html':
                fs.readFile(__dirname + path, function(error, data){
                    if (error){
                        response.writeHead(404);
                        response.write("opps this doesn't exist - 404");
                        response.end();
                    }
                    else{
                        response.writeHead(200, {"Content-Type": "text/html"});
                        response.write(data, "utf8");
                        response.end();
                    }
                });
                break;
            default:
                response.writeHead(404);
                response.write("opps this doesn't exist - 404");
                response.end();
                break;
        }
    });
    server.listen(8001);
```

Here we have a router with this code so we can visit the urls, but if you visit http://localhost:8001/socket.html, we will get some 404 message. If we consider this as our server.js and load reload http://localhost:8001, you can return the node server.js and see nothing new apart from “Hello World” output, let’s see what we’ve done line by line:

```
var url = require('url');
var fs = require('fs');
```

Here url is used for parsing and manipulating urls, fs  is the file handler, you can read about url here and fs here.

```
var path = url.parse(request.url).pathname;
```

This is simply the path followed by our domain, if you test this with adding console.log(path) line after this. So, localhost:8001 will assign ‘/’ and localhost:8001/a_path will assign ‘a_path’ to path.
Now for deciding on what we want the server to do, we do a switch case on the path. If it’s root path, the ‘hello world’ action is performed and if we want another action, it’s socket.html.

```
fs.readFile(__dirname + path, function(error, data){...});
```

Here we want to parse socket.html, we get a 404 message as it doesn’t exist. We want to open the file by fs module on the server receivable path. readFile here is for a callback function for defining its action like how we do the same in node.js, and the function here defines that action we want once we get the contents of the file.


```
if (error){
    response.writeHead(404);
    response.write("opps this doesn't exist - 404");
}
```
Now we want the 404 error to be solved. If we are unable to open the file or if it doesn’t exist, the error code is the passed argument to the readFile callback which contains the error code, the response to the error to be returned is a 404 message here to be returned, that would be our second variable passed if we open it.

```
else{
    response.writeHead(200, {'Content-Type': 'text/html'});
    response.write(data, 'utf8');
}
```

we have encoded the UTF8 for the document content for our readable file which is the same like we route to ‘/’.
We put response.end()  at the end of createServer function routed response object actions are closed and executed.
Now let’s fix the 404 message as we know the presence of it.
Adding Socket.io:
We want to remove the 404 error when we visit http://localhost:8001/socket.html so we are going to create a new page with socket.io, using socket.html
```
<html>
  <head></head>
  <body>This is our socket.html file</body>
</html>
```
The body tag here will be displayed when we visit socket.html after saving this file as server.js and run the node server module, but as we are here for the socket.io, let’s do that.
We will represent socket.io and extend it from server, we then tweak our server.js file like this:

```
var http = require("http");
var url = require('url');
var fs = require('fs');
var io = require('socket.io');
var server = http.createServer(function(request, response){
    var path = url.parse(request.url).pathname;
    switch(path){
        case '/':
            response.writeHead(200, {'Content-Type': 'text/html'});
            response.write('hello world');
            response.end();
            break;
        case '/socket.html':
            fs.readFile(__dirname + path, function(error, data){
                if (error){
                    response.writeHead(404);
                    response.write("opps this doesn't exist - 404");
                    response.end();
                }
                else{
                    response.writeHead(200, {"Content-Type": "text/html"});
                    response.write(data, "utf8");
                    response.end();
                }
            });
            break;
        default:
            response.writeHead(404);
            response.write("opps this doesn't exist - 404");
            response.end();
            break;
    }
});
server.listen(8001);
io.listen(server);
```

We have added io.listen(server), which means when our server listens the pages loaded by the WebSocket connection server when we open a listener for socket.io. Now when we run node server.js and reload http://localhost:8001/socket.html, nothing affects the browser but our server is now listening for anything change in websocket connections.
As it is listening to socket.io connections, we need something for the server to talk for listening, we have to provide a connection of WebSockets for socket.html page, we change that to:
```
<html>
  <head>
    <script src="/socket.io/socket.io.js"></script>
  </head>
  <body>
    <script>
      var socket = io.connect();
    </script>
    <div>This is our socket.html file</div>
  </body>
</html>
```
Now we have established a connection between client and server so that we can send information, in the above lines we have added the socket.io.js and a body script for client side connection.

Sending Data To The Client:
We have to use an ‘on’ method to map a name to any function. So that in order to send any data from server to socket.html, like in node.js, the data transmission of socket.io can be handled with callbacks. The execution of that function is by the ‘on’ method which simply uses the listener for Websocket connection, for which the mapping is done by the method name.
The opposite of on method is the emit method, which sends the arguments of mapped method name and the data for the function to either the client or the server. Add the following to server.js:

```
var listener = io.listen(server);
listener.sockets.on('connection', function(socket){
    socket.emit('message', {'message': 'hello world'});
});
```

When the function is executed, the ‘message’ action will be sent to the client as a json object {‘message’: ‘hello world’}, which is due to an emit action when the listener gets a ‘connection’ action call. When an io.connection(); is executed on socket.html as it has built in mappable actions when the action is triggered. When we add on method listener, the message the message action on socket.html is retrieved as per below:

```
var socket = io.connect();
socket.on('message', function(data){
    console.log(data.message);
});
```

With this you can send the data to the client side from server side by emit method. And by on method, the client side receives that data to write in the js console of the browser. If you run node.js and reload, we will get the hello world message and we will see debug statements from socket.io that explains transfer and content of the message in the command line.

We can easily produce the content through normal load or ajax call but we want the content to be continuous for this socket connection. Take the example of a running clock, where each second the information is changed, so we can achieve this through setInterval function where we can specify the time period for which it would take the content at that rate. In the following example, where we want to print the hello world message every second, you do:

```
setInterval(function(){
    console.log('hello world');
}, 1000);
```

We want to emit data for our clock through our socket connection with our server.js file:.

```
io.sockets.on('connection', function(socket){
    //send data to client
    setInterval(function(){
        socket.emit('date', {'date': new Date()});
    }, 1000);
});
```

We have setInterval inside the websocket connection callback, and we execute it every 1000ms, then:

```
socket.emit('date', {'date': new Date()});
```

We have setup date name and the listener on the client side receives JSON with a date. We made our socket connection send data repeatedly every 1000ms towards client side with on listener, the date is refreshed every second. Now we’ll update the client so as to receive our data.

```
<html>
  <head>
    <script src="/socket.io/socket.io.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.js"></script>  </head>
  <body>
    <script>
      var socket = io.connect();
      socket.on('date', function(data){
        $('#date').text(data.date);
      });
    </script>
    <div id="date"></div>
  </body>
</html>
```

This is nothing but a script to load jquery, so that we can display it when received. An id is used inside div so that it can be used with jquery, an ‘on’ method to receive data from the ‘emit’ method on the server. This ‘on’ method will thus simply receive an ‘emit’ data inside our date div, where the date is displayed due to these actions, restart the server and load the browser page, the date is displayed each second, but if you remove the 1000 from setInterval function, the default is 1 which means the data of the date is refreshed every millisecond! 
Sending Data From the Client To the Server:

As we learned the process of sending data from server to client, the process of the inverse is almost the same, taking an example let’s say we want to print and send every letter a user types in a textbox on a server console.
We will set up an emit function on the client side and an on listener on the server side, our socket.html should be:

```
<html>
<head>
  <script src="/socket.io/socket.io.js"></script>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.js"></script>
</head>
<body>
  <script>
  var socket = io.connect();
  socket.on('date', function(data){
    $('#date').text(data.date);
  });
  $(document).ready(function(){
    $('#text').keypress(function(e){
      socket.emit('client_data', {'letter': String.fromCharCode(e.charCode)});
    });
  });
  </script>
  <div id="date"></div>
  <textarea id="text"></textarea>
</body>
</html>
```

Here when something is entered in the text area added above, an emit event is triggered every time a key is pressed by the user whilst inside the text area. The String.fromCharCode(e.charCode) takes the character code of the key that triggered the event and converts it into a character string associated with the number code. 

Say if the ‘a’ key is triggered, then the JSON would be {'letter': 'a'}.Now we have to add the ‘on’ listener to our server.js file:

```
var listener = io.listen(server);
listener.sockets.on('connection', function(socket){
  //send data to client
  setInterval(function(){
    socket.emit('date', {'date': new Date()});
  }, 1000);
  //receive client data
  socket.on('client_data', function(data){
    process.stdout.write(data.letter);
  });
});
Notice that we first added:
//receive client data
socket.on('client_data', function(data){
  process.stdout.write(data.letter);
});
```

This is the listener for the client_data emit call, we will write the letter to the server console in JSON by triggering the listener. The process.stdout.write() is used here because it writes without adding a new line unlike console.log(). Try restarting the server and reload the page, we’ll have a clock running in the browser fetched from server and the real time text data entered in the text area being submitted to the command line.
Conclusion:

Hopefully, this tutorial has helped as an introductory for beginners who are interested in using node.js with socket.io. 

For any questions or queries feel free to contact me at iamnaveenpaul@gmail.com