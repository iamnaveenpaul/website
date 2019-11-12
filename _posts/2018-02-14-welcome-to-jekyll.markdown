---
layout: post
title:  "Node.js Tutorial With Socket.io"
date:   2019-11-07 00:56:34 +0900qu
categories: nodejs
---
It’s not an easy job to learn socket.io with node js at the same time, one reason to add is when someone who is trying to learn node js or is at an amateur level at it, he would be more likely interested in trying out all the features that the socket.io provide, also when someone is not familiar with the node.js, it’s protocol for WebSockets is left for himself to borrow it from random snippets of the code. 
<br><br>
On top of that, trying to parse its protocol while learning the socket.io library along with the basics of node js all at the same time becomes even more frustrating. I was shocked to see that there are no good quick tutorials on how to learn the basics of using socket.io with node js.

<br>
<p>
So I thought I would like to try to fill this void. Note that is updated to run on node 5.0.0 and socket 1.3.7 so I would recommend at least these versions for the code execution. We will cover the three steps in this tutorial. The first step is setting up a Node.js server and router, after this is connecting the socket.io to this server, and the final step is to send data to the client as well as server through that socket connection. Let’s begin..
</p>

<h3>Your Basic Server</h3>
We’ll use the http library module to initiate the server in Node.js, there are several kinds of modules we could apply and they all do the same job


{% highlight javascript %}
   var http = require('http');
   var server = http.createServer();
   server.listen(8001);
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
