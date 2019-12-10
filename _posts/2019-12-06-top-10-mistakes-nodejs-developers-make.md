---
title: Top 10 Mistakes Node.js Developers Make
image: "/assets/default-social-image.png"
categories: Node.js
---

**Introduction**

Node.js has seen tremendous growth in recent years, with it being embraced by large companies like Walmart or PayPal. The more people are picking up node and distributing NPM modules at a rate that goes [beyond other languages](http://www.modulecounts.com/). The theory of the Node, however, can take some time to get used to it, particularly if you changed from another language.

We're going to talk in this post about the most common mistakes node programmers make and how to eliminate them. For illustrations, you could find the source code on [github](https://github.com/alessioalex/airpair-nodejs-mistakes).

**#1. Not using development tools**

* nodemon or supervisor for automatic restart
* In-browser live reload (reload after static files and/or views change)

Unlike other languages like PHP or Ruby, once you make changes to the source code, node needs a reboot. One aspect that can slow you down while you're making web apps is reloading the browser when the code changes. Although these stuff can be done manually, there are better alternatives out there.

**Automating restarts**

Most of us are likely used to save a file in the editing document, click [CTRL+C] to interrupt and restart the program by clicking the [UP] arrow and [Enter] key. Nonetheless, you can automate this physical task and make things easier for development process by utilizing existing tools such as:

* [nodemon](http://nodemon.io/)
* [node-supervisor](https://github.com/isaacs/node-supervisor)
* [forever](https://github.com/nodejitsu/forever)

Monitoring for file updates and restarting the server for you is what these modules do. For instance, let's take nodemon. Next you install it all globally:

`npm i nodemon -g`

Simply swap the `node` command to the `nodemon` command:

```
  # node server.js

  $ nodemon server.js
  14 Nov 21:23:23 - [nodemon] v1.2.1
  14 Nov 21:23:23 - [nodemon] to restart at any time, enter `rs`
  14 Nov 21:23:23 - [nodemon] watching: *.*
  14 Nov 21:23:23 - [nodemon] starting `node server.js`
  14 Nov 21:24:14 - [nodemon] restarting due to changes...
  14 Nov 21:24:14 - [nodemon] starting `node server.js`
```

Probably the most popular choice among the current `nodemon` or `node-supervisor` options is to neglect specific files or folders.

**Automatic browser refresh**

You can also speed up implementation of web applications in addition to reloading the Node program when the source code shifts. Instead of manually activating the browser refresh page, we can also use tools such as [livereload](http://livereload.com/) to automate it.

They work similarly to those mentioned before, because in certain folders, they monitor for file changes so in this case, it initiatiates browser refresh (instead of restarting a server). The refresh is achieved either through a page-injected script or through a browser extension.

Rather than demonstrating you how to use livereload, we will build a similar tool for Node this time. It is supposed to do the following:

1. Check in a folder for file changes;
2. Send a message utilizing [server-sent events](http://html5doctor.com/server-sent-events/) to all associated clients;
3. Trigger the page reload.

First, the NPM dependencies required for the project should be installed:

* [express](http://npm.im/express) - To build a prototype web application
* [watch](http://npm.im/watch) - to monitor for any changes in file
* [sendevent](http://npm.im/sendevent) - server-sent events, SSE (an alternative might be websockets)
* [uglify-js](http://npm.im/uglify-js) - for minifying the client-side JavaScript files
* [ejs](http://npm.im/ejs) - view templates

Now we're going to create a basic Express server that renders the front page `home` view:

```
var express = require('express');
var app = express();
var ejs = require('ejs');
var path = require('path');

var PORT = process.env.PORT || 1337;

// view engine setup
app.engine('html', ejs.renderFile);
app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'html');

// serve an empty page that just loads the browserify bundle
app.get('/', function(req, res) {
res.render('home');
});

app.listen(PORT);
console.log('server started on port %s', PORT);
```

Because we use Express, we are also going to create the browser-refresh tool as a middleware for Express. The middleware must connect the endpoint of SSE and the client script will also build a view helper. Express `app` and the folder to be watched will be the reason for the middleware feature. As we realize that, before setting up the view (inside server.js) we can already put the following lines:

```
var reloadify = require('./lib/reloadify');
reloadify(app, __dirname + '/views');
```

We are looking for changes in the /views directory. For the middleware:

```
var sendevent = require('sendevent');
var watch = require('watch');
var uglify = require('uglify-js');
var fs = require('fs');
var ENV = process.env.NODE_ENV || 'development';

// create && minify static JS code to be included in the page
var polyfill = fs.readFileSync(__dirname + '/assets/eventsource-polyfill.js', 'utf8');
var clientScript = fs.readFileSync(__dirname + '/assets/client-script.js', 'utf8');
var script = uglify.minify(polyfill + clientScript, { fromString: true }).code;

function reloadify(app, dir) {
  if (ENV !== 'development') {
    app.locals.watchScript = '';
    return;
  }

  // create a middlware that handles requests to `/eventstream`
  var events = sendevent('/eventstream');

  app.use(events);

  watch.watchTree(dir, function (f, curr, prev) {
    events.broadcast({ msg: 'reload' });
   });

  // assign the script to a local var so it's accessible in the view
  app.locals.watchScript = '<script>' + script + '</script>';
}

module.exports = reloadify;
```

As you may have noted, the middleware won't do anything if the environment isn't set to 'development.' This ensures that for production, we won't have to eliminate it.

The frontend JS file is fairly simple, listening to the SSE messages and reloading the page when necessary:

```
(function() {

  function subscribe(url, callback) {
    var source = new window.EventSource(url);

    source.onmessage = function(e) {
      callback(e.data);
    };

    source.onerror = function(e) {
      if (source.readyState == window.EventSource.CLOSED) return;

      console.log('sse error', e);
    };

    return source.close.bind(source);
  };

  subscribe('/eventstream', function(data) {
    if (data && /reload/.test(data)) {
      window.location.reload();
    }
  });

}());
```

The eventsource-polyfill.js is the [polyfill for SSE by Remy Sharp](https://github.com/remy/polyfills/blob/master/EventSource.js). Last but not least, the only thing left to do is to use the view helper to include the script created from the frontend in the page (`/views/home.html`):

```
...
<%- watchScript %>
...
```

Each time you change the home.html page, the app must reload the server home page for you instantly (`http:/localhost:1337/`).

**2 Blocking the event loop**

Because Node.js runs on a single thread, it blocks everything that causes the event loop. That ensures that if you have a web server with a thousand linked clients and the event loop is interrupted, each client would just wait.

Here are some illustrations of how, maybe unknowingly you could do that:

* Parsing with the JSON.parse function, a huge [json payload](http://zef.me/4561/node-js-and-the-case-of-the-blocked-event-loop/);
* Trying to highlight syntax on the backend of a large file (with something like [Ace](https://github.com/ajaxorg/ace/blob/c5c1bb2b1305bfc08a899c96b2dac2ddad20d72a/demo/static-highlighter/server.js) or [highlight.js](https://github.com/isagalaev/highlight.js)); or
* Parsing a huge output in one go (such as the output of a [child process](http://nodejs.org/api/child_process.html) `git log` command).

The thing is you can do these stuff unknowingly, because it doesn't happen that often to decode a 15 Mb output, right? To grab you off-guard is enough for an attacker and the whole server will be DDOS-ed.

Luckily, to spot irregularities, you can track the event loop lag. This can be done either through proprietary tools like [StrongOps](http://docs.strongloop.com/display/SLA/Application+monitoring) or through the use of open-source modules like [blocked](http://npm.im/blocked).

The concept behind these tools is to [track the time](http://nodejs.org/api/process.html#process_process_hrtime) spent periodically between an interval and document it accurately. The time differential is determined by the period at moment A and moment B, the time at moment A is subtracted from moment B and the time interval is also subtracted.

Below is an example of how this can be done. It will do:

* Retrieve the gap between the present time and the time elapsed as a parameter for the high resolution;
* Determines the lag at regular intervals of the event loop;
* Displays the delay in green or red, in case it exceeds the threshold; then
* To see it in effect, a powerful computation is performed every 300 miliseconds.

The example's source code is as follows:

```
var getHrDiffTime = function(time) {
  // ts = [seconds, nanoseconds]
  var ts = process.hrtime(time);
  // convert seconds to miliseconds and nanoseconds to miliseconds as well
  return (ts[0] * 1000) + (ts[1] / 1000000);
};

var outputDelay = function(interval, maxDelay) {
  maxDelay = maxDelay || 100;

  var before = process.hrtime();

  setTimeout(function() {
    var delay = getHrDiffTime(before) - interval;

    if (delay < maxDelay) {
      console.log('delay is %s', chalk.green(delay));
    } else {
      console.log('delay is %s', chalk.red(delay));
    }

    outputDelay(interval, maxDelay);
  }, interval);
};

outputDelay(300);

// heavy stuff happening every 2 seconds here
setInterval(function compute() {
  var sum = 0;

  for (var i = 0; i <= 999999999; i++) {
    sum += i * 2 - (i + 1);
  }
}, 2000);
```

Until you operate it, you must install the [chalk](http://npm.im/chalk). You should see the results in the terminal after running the example.

As previously stated, current open source modules do the same, so use them confidently:

* [https://github.com/hapijs/heavy/blob/bbc98a5d7c4bddaab94d442210ca694c7cd75bde/lib/index.js#L70](https://github.com/hapijs/heavy/blob/bbc98a5d7c4bddaab94d442210ca694c7cd75bde/lib/index.js#L70)
* [https://github.com/tj/node-blocked/blob/master/index.js#L2-L14](https://github.com/tj/node-blocked/blob/master/index.js#L2-L14)

You will decide exactly which part of your program caused the delay if you pair this strategy with profiling.

**3 Executing a callback multiple times**

How many times have you saved a document and reloaded your Node web application to see it fail really quickly? The most likely scenario is that you made the callback twice, which implies that after the first time, you managed to forget the return.

Let's construct an instance for this scenario to reproduce. With some basic validation, we will create a simple proxy server. Execute the method and open (for instance) [http:/localhost:1337/?url=http:/www.google.com/](http://localhost:1337/?url=http://www.google.com/) to install the `request` dependency. For our case, the source code is the following:

```
var request = require('request');
var http = require('http');
var url = require('url');
var PORT = process.env.PORT || 1337;

var expression = /[-a-zA-Z0-9@:%_\+.~#?&//=]{2,256}\.[a-z]{2,4}\b(\/[-a-zA-Z0-9@:%_\+.~#?&//=]*)?/gi;
var isUrl = new RegExp(expression);

var respond = function(err, params) {
  var res = params.res;
  var body = params.body;
  var proxyUrl = params.proxyUrl;

  res.setHeader('Content-type', 'text/html; charset=utf-8');

  if (err) {
    console.error(err);
    res.end('An error occured. Please make sure the domain exists.');
  } else {
    res.end(body);
  }
};

http.createServer(function(req, res) {
  var queryParams = url.parse(req.url, true).query;
  var proxyUrl = queryParams.url;

  if (!proxyUrl || (!isUrl.test(proxyUrl))) {
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.write("Please provide a correct URL param. For ex: ");
    res.end("<a href='http://localhost:1337/?url=http://www.google.com/'>http://localhost:1337/?url=http://www.google.com/</a>");
  } else {
    // ------------------------
    // Proxying happens here
    // TO BE CONTINUED
    // ------------------------
  }
}).listen(PORT);
```

The above source code includes almost everything except the proxy itself, because I want you to look at it more closely:

```
request(proxyUrl, function(err, r, body) {
if (err) {
    respond(err, {
    res: res,
    proxyUrl: proxyUrl
    });
}

respond(null, {
    res: res,
    body: body,
    proxyUrl: proxyUrl
});
});
```

We handled the error condition in the callback, but after calling the respond function, we forgot to stop the execution flow. This implies that if we reach a domain that does not host a website, the respond function will be called twice and the following message will be displayed in the terminal:

```
Error: Can't set headers after they are sent.
    at ServerResponse.OutgoingMessage.setHeader (http.js:691:11)
    at respond (/Users/alexandruvladutu/www/airpair-2/3-multi-callback/proxy-server.js:18:7)

This can be avoided either by using the `return` statement or by wrapping the 'success' callback in the `else` statement:
```

```
request(.., function(..params) {
  if (err) {
    return respond(err, ..);
  }

  respond(..);
});

// OR:

request(.., function(..params) {
  if (err) {
    respond(err, ..);
  } else {
    respond(..);
  }
});
```

**4 The Christmas tree of callbacks (Callback Hell)**

They come up with the 'callback hell' argument any time someone wants to bash Node. Some see callback nesting as possible, but it's just false. There are a number of ways to maintain the script clean and easy, such as:

* Using control flow modules (like [async](http://npm.im/async));
* [Promises](http://strongloop.com/strongblog/promises-in-node-js-with-q-an-alternative-to-callbacks/); and
* [Generators](http://strongloop.com/strongblog/how-to-generators-node-js-yield-use-cases/).

To use the async module we must build a sample program and then refactor it. The app will serve as a naive resource analyzer which performs the following functions:

* Checks the amount of scripts/stylesheets/images in the HTML code;
* Outputs the terminal's total number;
* Checks every resource's content length;
* Put the total resource length into the terminal.

In contrast to the async module, the following npm modules will be used:

* [request](http://npm.im/request) for site data (body, headers, etc.).
* [cheerio](http://npm.im/cheerio) as backend jQuery (DOM selector element).
* [once](http://npm.im/once) to make sure you execute the callback once.

```
var URL = process.env.URL;
var assert = require('assert');
var url = require('url');
var request = require('request');
var cheerio = require('cheerio');
var once = require('once');
var isUrl = new RegExp(/[-a-zA-Z0-9@:%_\+.~#?&//=]{2,256}\.[a-z]{2,4}\b(\/[-a-zA-Z0-9@:%_\+.~#?&//=]*)?/gi);

assert(isUrl.test(URL), 'must provide a correct URL env variable');

request({ url: URL, gzip: true }, function(err, res, body) {
  if (err) { throw err; }

  if (res.statusCode !== 200) {
    return console.error('Bad server response', res.statusCode);
  }

  var $ = cheerio.load(body);
  var resources = [];

  $('script').each(function(index, el) {
    var src = $(this).attr('src');
    if (src) { resources.push(src); }
  });

  // .....
  // similar code for stylesheets and images
  // checkout the github repo for the full version

  var counter = resources.length;
  var next = once(function(err, result) {
    if (err) { throw err; }

    var size = (result.size / 1024 / 1024).toFixed(2);

    console.log('There are ~ %s resources with a size of %s Mb.', result.length, size);
  });

  var totalSize = 0;

  resources.forEach(function(relative) {
    var resourceUrl = url.resolve(URL, relative);

    request({ url: resourceUrl, gzip: true }, function(err, res, body) {
      if (err) { return next(err); }

      if (res.statusCode !== 200) {
        return next(new Error(resourceUrl + ' responded with a bad code ' + res.statusCode));
      }

      if (res.headers['content-length']) {
        totalSize += parseInt(res.headers['content-length'], 10);
      } else {
        totalSize += Buffer.byteLength(body, 'utf8');
      }

      if (!--counter) {
        next(null, {
          length: resources.length,
          size: totalSize
        });
      }
    });
  });
});
```

This doesn't seem too bad, but with nested callbacks you can go much further. You will remember the Christmas tree at the bottom from our previous example, where you can see indentation like this:

```
      if (!--counter) {
        next(null, {
          length: resources.length,
          size: totalSize
        });
      }
    });
  });
});
```

The following app can be executed by the command line:

```
$ URL=https://bbc.co.uk/ node before.js
  # Sample output:
  # There are ~ 24 resources with a size of 0.09 Mb.
```

Our code may look like the following after a bit of refactoring using async:

```
var async = require('async');

var rootHtml = '';
var resources = [];
var totalSize = 0;

var handleBadResponse = function(err, url, statusCode, cb) {
  if (!err && (statusCode !== 200)) {
    err = new Error(URL + ' responded with a bad code ' + res.statusCode);
  }

  if (err) {
    cb(err);
    return true;
  }

  return false;
};

async.series([
  function getRootHtml(cb) {
    request({ url: URL, gzip: true }, function(err, res, body) {
      if (handleBadResponse(err, URL, res.statusCode, cb)) { return; }

      rootHtml = body;

      cb();
    });
  },
  function aggregateResources(cb) {
    var $ = cheerio.load(rootHtml);

    $('script').each(function(index, el) {
      var src = $(this).attr('src');
      if (src) { resources.push(src); }
    });

    // similar code for stylesheets && images; check the full source for more

    setImmediate(cb);
  },
  function calculateSize(cb) {
    async.each(resources, function(relativeUrl, next) {
      var resourceUrl = url.resolve(URL, relativeUrl);

      request({ url: resourceUrl, gzip: true }, function(err, res, body) {
        if (handleBadResponse(err, resourceUrl, res.statusCode, cb)) { return; }

        if (res.headers['content-length']) {
          totalSize += parseInt(res.headers['content-length'], 10);
        } else {
          totalSize += Buffer.byteLength(body, 'utf8');
        }

        next();
      });
    }, cb);
  }
], function(err) {
  if (err) { throw err; }

  var size = (totalSize / 1024 / 1024).toFixed(2);
  console.log('There are ~ %s resources with a size of %s Mb.', resources.length, size);
});
```

**5 Creating big monolithic applications**

Programmers new to Node having worked with different language mindsets tend to do things differently. Of eg, including everything in one file and not breaking things into their own modules and uploading to NPM, etc.

Take, for instance, our previous case. We pushed everything into a single file, making checking and interpreting the code, challenging. But no worries, we can make it much better and more modular with some refactoring. In case you were wondering, this will also assist with 'callback hell'.

If we extract the URL validator, the response handler, the request functionality and the resource processor to their own files, our primary one will look like this:

```
// ...
var handleBadResponse = require('./lib/bad-response-handler');
var isValidUrl = require('./lib/url-validator');
var extractResources = require('./lib/resource-extractor');
var request = require('./lib/requester');

// ...
async.series([
  function getRootHtml(cb) {
    request(URL, function(err, data) {
      if (err) { return cb(err); }

      rootHtml = data.body;

      cb(null, 123);
    });
  },
  function aggregateResources(cb) {
    resources = extractResources(rootHtml);

    setImmediate(cb);
  },
  function calculateSize(cb) {
    async.each(resources, function(relativeUrl, next) {
      var resourceUrl = url.resolve(URL, relativeUrl);

      request(resourceUrl, function(err, data) {
        if (err) { return next(err); }

        if (data.res.headers['content-length']) {
          totalSize += parseInt(data.res.headers['content-length'], 10);
        } else {
          totalSize += Buffer.byteLength(data.body, 'utf8');
        }

        next();
      });
    }, cb);
  }
], function(err) {
  if (err) { throw err; }

  var size = (totalSize / 1024 / 1024).toFixed(2);
  console.log('\nThere are ~ %s resources with a size of %s Mb.', resources.length, size);
});
```

The functionality of the request can look like this:

```
var handleBadResponse = require('./bad-response-handler');
var request = require('request');

module.exports = function getSiteData(url, callback) {
  request({
    url: url,
    gzip: true,
    // lying a bit
    headers: {
      'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.111 Safari/537.36'
    }
  }, function(err, res, body) {
    if (handleBadResponse(err, url, res && res.statusCode, callback)) { return; }

    callback(null, {
      body: body,
      res: res
    });
  });
};
```

Note: in the [github repository](https://github.com/alessioalex/airpair-nodejs-mistakes), you can check the full instance.

It's easier to read stuff now, and we can start writing tests for our app. We may begin the refactoring cycle and also extract the functionality of the response length into its own module

The good thing about Node is that it allows you to write and publish small modules to NPM. You can find modules to create a random number between an interval and also for all kinds of things. In your node applications, you can aim for modularity and keep things as simple as possible.

[The one](http://substack.net/how_I_write_modules) from [substack](https://github.com/substack) is an interesting article on how to write modules.

**6 Poor logging**

Most node tutorials give you a small example containing `console.log` here and there, so some developers have had the idea that this is how logging into their application should be implemented.

If coding node apps, you should use something better than console.log, just because:

* No need for large, complex objects to use `util.inspect`;
* Built-in serializers for objects such as errors, requests and responses;
* Support multiple sources to verify where the logs are going;
* Automatic hostname inclusion, process id, name of the application;
* Supports multiple logging levels (debug, info, error, fatal, etc.);
* Advanced features such as rotation of log files, etc.

When using a production-ready logging module like [bunyan](https://github.com/trentm/node-bunyan/), you can get all those for free.Besides that, if you install the module globally, you also get a handy CLI tool for development.

Let's take a look at how to use one of their examples:

```
var http = require('http');
var bunyan = require('bunyan');

var log = bunyan.createLogger({
  name: 'myserver',
  serializers: {
    req: bunyan.stdSerializers.req,
    res: bunyan.stdSerializers.res
  }
});

var server = http.createServer(function (req, res) {
  log.info({ req: req }, 'start request');  // <-- this is the guy we're testing
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello World\n');
  log.info({ res: res }, 'done response');  // <-- this is the guy we're testing
});

server.listen(1337, '127.0.0.1', function() {
  log.info('server listening');

  var options = {
    port: 1337,
    hostname: '127.0.0.1',
    path: '/path?q=1#anchor',
    headers: {
      'X-Hi': 'Mom'
    }
  };

  var req = http.request(options, function(res) {
    res.resume();
    res.on('end', function() {
      process.exit();
    })
  });

  req.write('hi from the client');
  req.end();
});
```

If you run the terminal example, you'll see something like this:

```
  $ node server.js
  {"name":"myserver","hostname":"MBP.local","pid":14304,"level":30,"msg":"server listening","time":"2014-11-16T11:30:13.263Z","v":0}
  {"name":"myserver","hostname":"MBP.local","pid":14304,"level":30,"req":{"method":"GET","url":"/path?q=1#anchor","headers":{"x-hi":"Mom","host":"127.0.0.1:1337","connection":"keep-alive"},"remoteAddress":"127.0.0.1","remotePort":61580},"msg":"start request","time":"2014-11-16T11:30:13.271Z","v":0}
  {"name":"myserver","hostname":"MBP.local","pid":14304,"level":30,"res":{"statusCode":200,"header":"HTTP/1.1 200 OK\r\nContent-Type: text/plain\r\nDate: Sun, 16 Nov 2014 11:30:13 GMT\r\nConnection: keep-alive\r\nTransfer-Encoding: chunked\r\n\r\n"},"msg":"done response","time":"2014-11-16T11:30:13.273Z","v":0}
```

But it's easier to use the CLI method in production.

Bunyan provides you with a lot of useful information about the current production cycle that is important. Another useful feature is that you can pipe the logs (or several streams) into a stream.

**7 No tests**

When we did not write any evaluations for them, we should never find our applications 'done'. Considering how many existing tools we have for that, there's really no excuse for them:

Testing frameworks: [mocha](https://github.com/mochajs/mocha), [jasmine](https://github.com/pivotal/jasmine), [tape](https://github.com/substack/tape) and much more
Assertion modules: [chai](https://github.com/chaijs/chai), [should.js](https://github.com/shouldjs/should.js)
Modules for mocks, spies, stubs or fake timers like [sinon](http://sinonjs.org/)
Code coverage tools: [istanbul](https://github.com/gotwarlost/istanbul), [blanket](https://github.com/alex-seville/blanket)

The rule for NPM modules is that in your `package.json`, for instance, you define a test command:

```
{
  "name": "express",
  ...
  "scripts": {
    "test": "mocha --require test/support/env --reporter spec --bail --check-leaks test/ test/acceptance/",
    ...
 }
```

Then analysis can be done with `npm test`, irrespective of the testing framework used.

Another thing that you should consider for your plans is to enforce before committing all of the tests. Thankfully it's as easy as `npm i pre-commit --save-dev`.

You can also choose to impose a certain degree of code coverage and reject commits that do not meet that standard. The pre-commit module would simply run `npm test` as a `pre-commit` hook automatically tests for you.

If you're not sure how to start writing tests, you can either find online tutorials or browse Github's popular node projects, such as:

[express](https://github.com/strongloop/express/tree/master/test)
[loopback](https://github.com/strongloop/loopback/tree/master/test)
[ghost](https://github.com/TryGhost/Ghost/tree/master/core/test)
[hapi](https://github.com/hapijs/hapi/tree/master/test)
[haraka](https://github.com/baudehlo/Haraka/tree/master/tests)

**8 Not using static analysis tools**


Instead of finding production problems, by using static analysis tools, it is better to catch them in progress instantly.

Tools like [ESLint](http://eslint.org/) help to solve a broad range of problems including:

* Potential errors for instance: disallow assignment in conditional sentences, disallow `debugger` usage.
* Following best practices as eg: disallow the use of `arguments.callee` to assert the same variable more than once.
* Finding potential security issues like using `eval()` or [regular expressions](https://blog.liftsecurity.io/2014/11/03/regular-expression-dos-and-node.js) that are not safe.
* Pinpointing potential performance problems.
* Implementing a concise guide to style

For a more detailed set of rules, check out the documentation section for the [ESLint rules](http://eslint.org/docs/rules/). If you want to set up ESLint for your task, you should also read the [setup](http://eslint.org/docs/configuring/) files.

If you wondered where to locate a sample configuration file for ESLint, there's one for the [Esprima project](https://github.com/ariya/esprima/blob/master/.eslintrc).

Other similar linting tools like [JSLint](http://www.jslint.com/) or [JSHint](http://www.jshint.com/) are out there.

Try [Esprima](http://esprima.org/) or [Acorn](https://github.com/marijnh/acorn) in case you want to decode the AST (abstract source tree) and construct a static analysis tool on your own.

**9 Zero monitoring or profiling**

You are left out of the loop by not monitoring or evaluating a node query. You don't care about important things like activity loop lag, CPU load, device load, or storage use.

There are proprietary services, such as [New Relic](http://newrelic.com/nodejs),  [AppDynamics](https://docs.appdynamics.com/display/PRO39/APM+Overview+-+Node.js), [StrongLoop](http://strongloop.com/node-js/monitoring/) or [Concurix](http://concurix.com/), that take care for you about these things.

You can also do this by using open source modules like [look](https://github.com/baryshev/look) or by gluing different NPM modules on your own. Ensure that you're always mindful of your application's condition at all stages with whatever you prefer, unless you want to answer odd midnight phone calls.

**10 Debugging with console.log**

It's easy to just add `console.log` in some ways and monitor when something goes wrong. You delete the `console.log` testing leftovers until you find out the issue and start.

The challenge is that it may come along with the next programmer, or even yourself to repeat the cycle. That's why there's a device called [debug](http://npm.im/debug). You should overwrite it with the `debug` feature and just leaving it there instead of adding and removing `console.log` script.

Using the variable of `DEBUG` environment, the next person starts the app, to figure out the issue.

This tiny module possesses its advantages:

* Nothing will be shown in the console when you launch the app using the DEBUG environment variable.
* The code sections can be randomly debugged (even with wildcards).
* The output in your terminal is perfectly painted.

Let's look at the official example of them:

```
// app.js
var debug = require('debug')('http')
  , http = require('http')
  , name = 'My App';

// fake app

debug('booting %s', name);

http.createServer(function(req, res){
  debug(req.method + ' ' + req.url);
  res.end('hello\n');
}).listen(3000, function(){
  debug('listening');
});

// fake worker of some kind

require('./worker');

<!--code lang=javascript linenums=true-->

// worker.js
var debug = require('debug')('worker');

setInterval(function(){
  debug('doing some work');
}, 1000);
```

Nothing arises if we execute the instance with node app.js, however if we include the DEBUG flag, it works flawlessly.

You can also use it for small modules that are published to NPM in addition to your applications. As with a more sophisticated logger, it can only do and will do the debugging job quite pretty well.