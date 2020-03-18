---
title: What's New for Node.js in 2020
image: "/assets/default-social-image.png"
---

In 2019, Node.js turned 10 years old, and the number of packages available on npm crossed one million. Downloads for Node.js itself continues to rise, growing 40% year over year. Another significant milestone is Node.js recently joined the OpenJS Foundation, which promises to improve project health and sustainability, as well as improve collaboration with the JavaScript community at large.

As you can see, a lot has happened in a relatively short amount of time! Every year the Node.js community has gained momentum, and 2020 shows no signs of slowing down.

There are lots of interesting features being explored for the next major releases of Node.js. In this post I’ll explore some of the most significant updates the Node.js community can expect in 2020.


# What’s New in Node.js Version 13?
As of this writing, the most recent release of Node.js is 13. There are already a number of features and updates we can start playing around with leading into 2020. Here’s a list of highlights:

* ECMAScript modules
* WebAssembly support
* Diagnostic reports
* Full internationalization support for date, time, number, and currency formats
* QUIC protocol support
* V8 JavaScript engine performance updates


# Support for ECMAScript Modules
As of v13.2.0, Node.js supports both traditional CommonJS modules and the new standard ECMAScript (ES) modules out of the box. This means you can finally use import and export syntax you may already be using for client-side JavaScript running in the browser. Also, it’s important to note ES modules in Node.js have JavaScript strict mode enabled by default, so you don’t have to specify "use strict"; at the top of every file.

```
// message file
async function sendMessage { ... }
export { sendMessage };

// index file
import { sendMessage } from "./message";

```

However, you still need to do a little work to let Node.js know you are using ES modules. The two most common ways to do this are using the .mjs file extension or specifying "type": "module" in the nearest parent package.json file.

Option 1: Rename .js files to .mjs files.
Option 2: Update the root package.json file, or add a package.json to the folder that contains ES modules and specify the type as module.

```
{
   "type": "module"
}
```

Another possibility is enabling ES module in the root package.json file, and then renaming all CommonJS module files to use the .cjs extension.

Personally, I find the .mjs and .cjs extensions a little gross, so I’m glad to see there are ways of specifying ES and CommonJS module usage with a package.json file.


# Node.js can Import WebAssembly Modules
Along with ES module support comes the ability to import WebAssembly (Wasm) modules! A WebAssembly module is a portable compiled binary format that can be parsed faster than JavaScript and executed at native speeds. WebAssembly modules can be created using a language such as C/C++, Go, C#, Java, Python, Elixir, Rust, and many others.

WebAssembly module support is still in the experimental stage as of this writing. To enable the feature, you must pass a command-line flag when executing a Node.js application. For example:

`node --experimental-wasm-modules index.js`

As an example, imagine you have an image processing library implemented as a WebAssembly module. The syntax for using this Wasm module might look like the following.

```
import * as imageUtils from "./imageUtils.wasm";
import * as fs from "fs";
( async () => {
   const image = await fs.promises.readFile( "./image.png" );
   const updatedImage = await imageUtils.rotate90degrees( image );
} )();
```

It’s also possible to import a WebAssembly module using the new dynamic import() statement in Node.js.

```
"use strict";
const fs = require("fs");
( async () => {
   const imageUtils = await import( "./imageUtils.wasm" );
   const image = await fs.promises.readFile( "./image.png" );
   const updatedImage = await imageUtils.rotate90degrees( image );
} )();
```

# WebAssembly System Interface (WASI)

Similar to JavaScript, WebAssembly is designed with security in mind to prevent access to any of the underlying operating system, sometimes referred to as “sandboxed.” However, there are times when a WebAssembly module in your control in Node.js may benefit from being able to make system-level calls.

This is where the new WebAssembly System Interface (WASI) comes in. WASI is designed to be a standard interface for making calls to the underlying system, such as the host application, native operating system, and so forth.

Initial WASI support was recently committed to the Node.js project. WASI is another exciting feature we may see come to Node.js in 2020!

# Internationalization Support Expands in 2020
As of v13.x, Node.js comes compiled with full ICU (International Components for Unicode). ICU is a mature and popular globalization library. Among many features, ICU includes support for formatting numbers, dates, times and currencies, performing time calculations and string comparisons, and converting text between Unicode and other character sets.

# Other Node.js Updates for 2020
QUIC protocol support: a modern transport for connected applications with increased performance and reliability.
Better Python 3 build support: in 2020 it should be possible to build Node.js and native modules using Python 3.
An Updated V8 JavaScript engine: V8 v7.8 and 7.9 increase performance and Wasm support.
Stable Workers Threads API: Worker threads in Node.js enable parallel, CPU-intensive JavaScript operations.


Learn More about Node.js, JavaScript, and Security
This post only begins to scratch the surface of all the hard work going into improving Node.js in 2020! If you’re interested in staying informed of the latest changes or getting involved in some way, there is a list of ways to contribute to Node.js on the Node.js web site.