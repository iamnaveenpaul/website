---
image: "/assets/default-social-image.png"
title: A blazing fast Express server with these 5 easy steps
---

# Introduction
Express is the one of most popular web frameworks and the top framework by a long mile for a NodeJs application.
Its easy to use and at the same time with right configuration we can make it a very fast light weight webserver.

# gzip Compression
Compressing your page content can reduce page size by up to 70%! I was testing an app with 8mb angular app after production build and deployment. The app used to take lot of time to load. Sometimes as much as 60 seconds on a good broadband network.

With the recent Covid lockdown, lots of my customers started working fronm home using mobile internet and many complained the app won't even load for them. After investigating, I stumbled that I had compltely missed compressing the static file! I used the follow code after installing compression module and it improved the speed manifold. The app size over the network reduced from 8mb to 2mb and I was able to use this on even 3G speeds.

```
var compression = require('compression');
var express = require('express');

var app = express();

app.use(compression());
```

# Use Cache-Control
Usually for complex enterprise grade apps, one would setup CDN or AWS cloudfront static files distribution to multiple locations around the global to improve faster access of the app. But just doing cachin on the expresse server also improves the performance by a huge margin.  For assigning app-wide cache settings, use:

```
var express = require('express');
var app = express();

app.use(express.static(__dirname + '/public', { maxAge: 31557600 }));
```

This will assign the cache settings for everything in the public directory. For more fine-grained control, you can set caching based on individual requests/routes:

```
var express = require('express');
var app = express();

app.get('/index.html', function (req, res) {
	res.setHeader('Cache-Control', 'public, max-age=86400');
	res.render('index.html');
});
```

# Run Express in Production Mode
By default, Express will run in development mode, which is easy to overlook, especially for those just starting out with Node.js/Express.

So, whats the difference between production and development mode anyway? Turns out, in development mode the view templates are read from a file for each request, whereas in production mode the templates are loaded once and cached. This is done so you can easily make changes on the fly without having to restart the app every time during development. In a production environment, however, this can greatly reduce your performance since you have to deal with slow file IO as compared to much faster RAM.

Lucky for you, getting Express in to production mode is easy. It's just a matter of setting an environment variable.

`$ export NODE_ENV=production`

Be careful with this method though. If the server restarts, you'll lose this environment variable and go back to using development mode. A more permanent solution is to set the variable within your .bash_profile:

```
$ echo export NODE_ENV=production >> ~/.bash_profile
$ source ~/.bash_profile
```

# Minify with Uglify
For just about every website, especially those with lots of styling and client-side functionality, static assets can be a huge drag on performance. Having to send over multiple JavaScript and CSS files for each request eventually takes its toll on your server, and that's not even considering the time the user has to wait for all the separate HTTP requests to finish on the client side.

To help mitigate this, you can use a utility package like Uglify to minify and concatenate your JavaScript and CSS files. Combine this with a task runner like Grunt and you'll easily be able to automate the process and not have to worry about it. A fairly capable Grunt file (using the grunt-contrib-uglify plugin) might look something like this:

```
module.exports = function(grunt) {

	grunt.initConfig({
		uglify: {
			options: {
				banner: '/*! <%= pkg.name %> <%= grunt.template.today("dd-mm-yyyy") %> */\n'
			},
			dist: {
				files: {
					'dist/<%= pkg.name %>.min.js': ['<%= concat.dist.dest %>']
				}
			}
    	}
	});

	grunt.loadNpmTasks('grunt-contrib-uglify');
	grunt.registerTask('default', ['uglify']);
};
```

# Increase Max Sockets
By default the Node.js HTTP server has a socket pool limit of only 5. This is a very conservative number and most servers can handle a much higher number of sockets than this.

Alternatively, you can allow as many sockets as possible:

```
var http = require('http');
var https = require('https');

http.globalAgent.maxSockets = Infinity;
https.globalAgent.maxSockets = Infinity;
```