---
image: "/assets/default-social-image.png"
title: What is npm?
categories: Npm
---

Npm is a package manager for the JavaScript programming language (originally short for Node Package Manager). It is the default package manager for the Node.js runtime environment for JavaScript. This consists of a command line server, also known as npm, and a free and paid-for personal package online database called the npm registry. The registry is accessed via the client and it is possible to browse and search through the npm website for the available packages. Npm, Inc. manages the package manager and the registry.

It’s the world’s largest software registry/library containing over 800,000 code packages. Open source developers use npm to share software and many organizations to manage private development, you can download all npm public software packages without any registration or logon.

**Command Line Client**

A CLI (Command Line Client) is included in npm which can be used to download and install software:

Windows Example

`C:\>npm install <package>`

Mac OS Example

`>npm install <package>`

**Installing npm**

To get npm installed on your computer, you have to install Node.js. Download Node.js from the official Node.js [website](https://nodejs.org/).

**Software Package Manager**

The name npm (Node Package Manager) comes from the first time that npm was developed as Node.js package manager and all npm packages are defined in files called package.json, and the content must be written in JSON. The definition file must contain at least two fields: name and version.

Example:

```
{
"name" : "foo",
"version" : "1.2.3",
"description" : "A package for fooing things",
"main" : "foo.js",
"keywords" : ["foo", "fool", "foolish"],
"author" : "John Doe",
"licence" : "ISC"
}
```

**Managing Dependencies**

npm can manage dependencies and can install all the project dependencies (also defined in package.json) in one command line.

**Sharing Your Software**

You can sign in at [npmjs.com](https://www.npmjs.com/) if you want to share your own software in the npm registry.

**Publishing a Package**

As long as the directory has a package.json file, you can publish any file/directory from your machine.

To check if npm is installed with:

`C:\>npm`

To check if you are logged in with:

`C:\>npm whoami`

If you are not logged in, log in with:

```
C:\>npm login
Username: <your username>
Password: <your password>
```

Navigate and publish your project with:

```
C:\Users\myuser>cd myproject
C:\Users\myuser\myproject>npm publish
```