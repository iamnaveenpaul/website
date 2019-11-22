---
image: "/assets/default-social-image.png"
categories: Naveen_Paul
title: How To Install Node.js on Ubuntu 16.04
---

**Introduction**

Node.js is a JavaScript platform that executes the JS code outside browser and lets developers write command line tools and for server-side scripting to produce dynamic web page content before the page is sent to the browser. It represents a "JavaScript everywhere" paradigm, unifying web-application development around a single programming language, rather than different languages for server and client side scripts. Developed by Linux, it is a general programming language that aims to optimize scalability with many operations, real time web applications and building quick network applications, making development more consistent and designed within the same system by leveraging JS on both front and back end.

In this guide, we’ll show you how to get started with Node.js on an Ubuntu 16.04 server.

**Prerequisites**

Before we begin, make sure you are using Ubuntu 16.04 and have a non root user account with sudo privileges set up, it is recommended to do this first by completing steps 1-4 in the initial Ubuntu server setup.

**How To Install the Distro-Stable Version for Ubuntu**

Ubuntu 16.04 can be used to provide consistent experience across multiple platforms because it has the suitable version of Node.js in it default repositories. The repositories could be any latest version and the current v4.2.6 as of now is sufficient for stable and quick experimentation.

We have to use the apt package manager in order to get this version, first by refreshing local package index and installing it from the repositories

```
sudo apt-get update

sudo apt-get install nodejs
```

If this suits your needs, it’s sufficient to set up with Node.js but in many cases, you also want to also install npm package manager which allows you to install modules and packages to use with Node.js easily and conveniently.

`sudo apt-get install npm`

Note that the name of executable package from the Ubuntu repositories is called nodejs instead of just node as to avoid conflict with another package.

Check the version of the installed Node.js, Once you got to know the version, you have the option to decide to work with different versions, version managers and package archives.

`nodejs -v`

Next, we’ll discuss more flexible and robust methods of installation.

**How To Install Using a PPA**

Also, you can add a PPA (personal package archive, maintained by NodeSource) to get a more recent version of Node.js, which will have more up-to-date versions of Node.js than the official Ubuntu repositories where you can choose between Node.js v4.x (supported until April of 2018), Node.js v6.x (supported until April of 2019), and Node.js v8.x (the current LTS version, supported until December of 2019).

For installing PPA, make sure that you’re in your home directory and use curl to retrieve the script for installation to the preferred version you want and replace 8.x with your preferred version string (if different)

```
cd ~

curl -sL https://deb.nodesource.com/setup_8.x -o nodesource_setup.sh
```

You can inspect the script content with any text editor. Here we’ve used nano.

```
nano nodesource_setup.sh

sudo bash nodesource_setup.sh
```

We run the script under sudo, the PPA will be installed and the local package cache and configuration will be automatically updated. You can install the Node.js package in the same way you did above after running the setup script from nodesource.

```
sudo apt-get install nodejs

nodejs -v

Output

v8.10.0
```

We have checked the node.js version after the initial steps, the package already contains the Node.js npm and binary, which keep track of updates in your home directory using a configuration file which will be created the first time you run npm.

`npm -v`

This line is used to verify that npm is installed and create the configuration file.

```
Output

5.6.0
```

You will need to install the build-essential package in order for some npm packages to work (those that require compiling code from source as an example)

`sudo apt-get install build-essential`

For compiling code from source, you have now necessary tools to work with npm packages.

**How To Install Using NVM**

A nvm (Node.js version manager) tool works within your home directory at the level of an independent directory which is an alternative to installing Node.js through apt. You can install multiple, self-contained versions of Node.js without affecting the entire system.

With nvm environment, you have the access of the newest versions of Node.js while retaining and managing previous releases. It is different from apt-get in the sense that it is distinct from the distro-stable version of Node.js available from the Ubuntu repositories.

The nvm will leverage these tools to build the necessary components, so we need to get the software packages from our Ubuntu repositories that will allow us to build source packages.

```
sudo apt-get update

sudo apt-get install build-essential libssl-dev
```

You can pull down the nvm installation script from the project’s GitHub page, once the prerequisite packages are installed, the version number may be different.

`curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh -o install_nvm.sh`

Here, we have downloaded it with the curl, now with nano, inspect the installation script.

```
nano install_nvm.sh

Using bash, run the script.

bash install_nvm.sh
```

The software is installed into a subdirectory of your home directory at ~/.nvm and it will also add the necessary lines to your ~/.profile file to use it.

You’ll need to log out and log back in again for gaining access to the nvm functionality or also you can source the ~/.profile, so that the changes are reflected to the current session

`source ~/.profile`

You can now install isolated Node.js versions. To find out the versions of installable Node.js that are available, use,

```
nvm ls-remote

Output

...

v8.5.0

v8.6.0

v8.7.0

v8.8.0

v8.8.1

v8.9.0   

v8.9.1   

v8.9.2   

v8.9.3   

->      v8.9.4   (Latest LTS: Carbon)        
```

So, the newest LTS version at this was is v8.9.4, as you can see. For installing it, use
nvm install 8.9.4

Usually, nvm will use the recent installed version. But, you can also explicitly tell nvm to use the latest version you just downloaded by,

`nvm use 8.9.4`

By using nvm, when you installed Node.js, the executable is called node. You can see the current version of it being used by the shell by,

```
node -v

Output

v8.9.4
```

You can see what is installed when you have multiple versions present by,

`nvm ls`

If you wish to default any one amongst them,

`nvm alias default 8.9.4`

You can also reference it by the alias but this version will be automatically selected when the current session ends.

`nvm use default`

For its own packages, each version of Node.js will keep track off with npm to manage it.

In the Node.js project’s ./node_modules directory, you can have npm install packages with normal format like express module,

`npm install express`

If you want to install it in such a way that it makes it available to the other projects using the same Node.js version), you can add the -g flag,

`npm install -g express`

The package will be installed in:

`~/.nvm/node_version/lib/node_modules/package_name`

By installing it globally like this, you will be able to run the commands direct from the command line, but for that, first you have to package the link into your local sphere to require it from within a program

`npm link express`

With nvm, the help options you can get with it can be seen by,

`nvm help`

**Removing Node.js**

Depending on the version you want to remove, you can uninstall Node.js by either apt-get or nvm and you will need to work with the apt-get utility at the system level to remove the distro-stable version,
sudo apt-get remove nodejs

This will remove the package but the configuration files are retained, useful when you intend to install the package again later. If you don’t want to save the configuration files and uninstall the package completely,
sudo apt-get purge nodejs

You can remove any unused packages that were automatically installed with the removed package:

`sudo apt-get autoremove`

To uninstall a Node.js version that you have enabled using nvm, you need to determine first the version you would like to remove is the current active version or not,

`nvm current`

If the version is not the currently active,

`nvm uninstall node_version`

This command will uninstall the selected version of Node.js.

If the version is the current active version, you must first deactive nvm to enable your changes to remove that version

`nvm deactivate`

This will remove all files associated with the version of Node.js except the cached files which can be used for reinstallment.

**Conclusion**

That was quite a work for running with Node.js on your Ubuntu 16.04 server. The easiest was the packaged version in Ubuntu’s repository, the nvm method of installation is definitely much more flexible. But circumstances might dictate others at some point.