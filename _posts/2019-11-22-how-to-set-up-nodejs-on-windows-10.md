---
title: How to set up Node.js on Windows 10
image: "/assets/default-social-image.png"
categories: Nodejs-Windows
---

**In this article, I will show how to set up Node.js on windows 10**

The main we will be focussing right now is to set up a developer environment for Node.js project, not running it.

**Preparation**

Working with Node.js on Windows has become better than four or five years ago, where it was too cumbersome and frustrating, that’s why it was difficult to choose between Windows 7 or 10 for our purpose.

Now, even though Windows 10 is made its way into the market but it still has some negativity such as metrics and extensive data collections, but it’s only logical to go with it even though Windows 7 might still be popular, the one reason that we need to have, apart from the newest technology and tools is an up to date operating system which is very crucial for security and other reasons. That's one reason for which we will use the newest tools and applications available and we will use the 64 bit version of all, which might not be possible for most cases but it’s also important not to let the tools fall behind.

We’ll be setting the Node.js on Windows 10 machine and also, I’ll check out the project and run it for which I am currently working on that depends on pg, koa and other modules. I will also cover the deployment to Azure later, but all of this is beyond the scope of this tutorial. Installing everything will be done natively and I wouldn’t recommend Cygwin for Node. While it’s free to use the VirtualBox, I had problems with running Linux on Windows engine.

**Step 1: Install Git**

We’ll [install Git](https://git-scm.com/download/win) first and use the default settings the way they are because they are quite sensible.

To set your projects folder in your home directory, select “Git bash here” by right clicking and check the version by `git --version`.

Create a .bash_profile as this a nice environment for bash and when you open a bash window, it is going to be executed. Click on the upper left corner as this is not cmd.exe window. You can post the text by clicking the middle mouse button like the Linux terminals.

**Step 2: Install Node.js on Windows 10**

Download and install the LTS version of [Node.js](https://nodejs.org/en/download/).

Since the node version manager (NVM) does not officially support Windows, I don’t recommend installing multiple versions side by side. Installing node utilities globally with different versions could be a problem, even though there are alternatives like [nvm-windows](https://github.com/coreybutler/nvm-windows) or [nodist](https://github.com/marcelklehr/nodist).

**Step 3: Update npm**

The package manager, npm will be automatically available after installing Node.js.

Open a bash shell and check the npm version with `npm --version`, and upgrade it ti the latest version available, this is important for handling peer dependencies for our purposes). Open the start menu, search for Power Shell and run it as an Administrator and follow [these](https://github.com/felixrieseberg/npm-windows-upgrade#usage) three steps.

**Step 4: Install Visual Studio and Python**

We have to install Visual Studio as the node packages depend on the native code to some extent. The supported tools for windows platform is the Visual Studio which is supported, the node gyp is around Python’s ‘generate your projects or GYP which generates project files for Visual Studio, Xcode and Gcc.

**Install Python (version 2.x or above)**

Download and install [this](https://www.python.org/downloads/windows/) Python (2.x branch for x64) and choose the default settings, select the ‘add to path’ option’ which will add its binary to global path. So, you have to reenter the session or log out and log back in.

**Install Visual Studio (2015)**

Select the system, select advanced settings, go to environment variable settings  and add the GYP_MSVS_VERSION=2015 to the global, we will be installing Visual Studio (VS2015) 2015 for our purposes, because it works fine with Node.js x64. Also, for Windows 10, we are going to follow the [Node-gyp tutorial](https://github.com/nodejs/node-gyp).

[Download](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) the Visual Studio 2015 Community Edition, unless you have the full VS machine. The, choose custom installation and select all Visual C++ branch but without XP support, choose Windows SDKs from tools. Don’t worrk as of now, you can reinstall or repair by reinstalling VS2015 if in case anything goes wrong.

**Step 5: Install Package Dependencies**

I am currently working on the alerting microservice in [Trace](https://trace.risingstack.com/), so I’ll install our package dependencies by `npm -i`.

I was working on alerting microservice and I was getting the above,. Here, the warning is for OSX only, the rest modules are fine, fsevents is optional and is for OSX only.

I installed Erlang along with this microservice as this uses Postgres and RabbitMQ. A package manager, similar to apt, Chocolatey or many others is OSX brew and rocket service manager setup, thing is I had to [manually enable](https://www.rabbitmq.com/management.html) the web admin on port 15672, which is the only difference.

I added my default user and created a database on the database part, but all that could be done effortlessly from the PgAdmin client.

**Step 6: Handling Environment Variables**

As Node.js projects are highly dependent on environment variables.

The env var, IS_INTERACTIVE is very easy to define on Linux and OSX, but works a bit differently on Windows.

With `npm -g`, I recommend avoiding installing packages globally, You can use locally installed node modules in the scripts section of the package.json. Also, we have many other options but I don’t recommend adding env vars directly to the scripts section on Windows (or rather in a cross-platform team).

Npm passes on these commands [directly to the OS](https://github.com/npm/npm/issues/4040), in this case to the NT command interpreter (cmd.exe).

Copy the script line into our bash window and run it there, because the npm passes on these commands directly to the OS, in this case to the NT command interpreter (cmd.exe), this would be the quickest way to fix it but this won’t work as a long-term solution. The [bash shell support](http://insights.ubuntu.com/2016/03/30/ubuntu-on-windows-the-ubuntu-userspace-for-windows-developers/) in Windows will probably solve this issue.

Use one command per script line, our `npm run lint` command here will work just fine.

If anything that relies on temporary env variables called flashvars or does a lot of things at once will go as Node executable JavaScript files to /scripts folder.

The cmd can’t handle bash scripts, so avoid them, the Cmd.exe supports && so two or three commands may be fine, but avoid writing full shell script in a line, especially with its features. we will need lots of env vars to run our application but this is okay for support scripts.

We use [nodemon](https://github.com/remy/nodemon) during development at RisingStack, it is a file watcher where one can define env vars parses the nodemon.json file upon start.

Do not forget to initialize nodemon with `git config --global core.excludesfile ~/.gitignore_global` in .gitignore_global file in the home directory, in my project I can have multiple nodemon json templates this way.

It's easier just to manually launch nodemon during development, and not via the appropriate run script. But it’s not elegant solution to install nodemon globally. 

I can now start up my microservice with the above json

I export each and every env var on my convert the nodemon.js onto a nodemon.sh, where nodemon is not the best solution for just running scripts since I don’t want to watch for the changes in the files. Note to add it to the ignore file as pushing this file accidentally into a repo can be frustrating, so don’t forget this.

```
export NODE_ENV="development"

export PORT=3060

export AMQP_URI="amqp://localhost:5672/"

export EMAIL_SENDER_NAME="Developer"

#etc.
```

Since it would be easy to convert it to a traditional bat file as our DB setup needs a couple of env vars and I don't want to watch it with this quick but not so handsome way. I run it locally but I would set up the env vars properly on a cloud provider, instead of sourcing it on the command line (source nodemon.dev.sh) for the MinGW bash we are using.

The project should now work, like on the Linux or OSX. The Windows might not have the compatibility to support some of the modules in npm, but things are improving as they have some nice and friendly GUI tools and on top of that, Visual Studio can be a powerful asset. This may be a viable option for those who don’t mind working some more to this to achieve.

We covered our short tutorial on using Node.js on Windows 10.