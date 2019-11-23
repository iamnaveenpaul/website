---
title: Running NodeJS on Linux on Windows (with no VM)
image: "/assets/default-social-image.png"
categories: Nodejs-Windows
---

Hello [Windows](https://hackernoon.com/tagged/windows) using web developers, now you can run [Linux](https://hackernoon.com/tagged/linux) Bash in Windows and get `emacs` and `vi` and `ssh` as well as anything else that could float your boat. In your dream little black window right there.

I am opening command prompt (Windows), entering Bash (Linux), running a Node server (Linux) on localhost and opening that in Chrome (Windows), that’s what you could see in the gif below

It's called WSL (Windows Subsystem for Linux). There are some specifications for the program. I know you’ll figure that out on your own.

**WSL in action**

I'm using Node's `os` module framework `platform()` method to print the platform name so you know this is Windows. Yes, I'm starting with a good old-fashioned command prompt. I run a `node` that runs the Node instance I installed in of course, Windows.

Then I leave the Linux node and run `bash`. As I'm in a bash for Linux, I now run `node` again, so it's the node instance I've built for this instance of Linux (we'll get to the instructions below).

Now I see that I'm on Linux when I type `os.platform()`. Great! `Ctrl+D` will break out of the node, then break me out of Linux again and return to the Windows command prompt.

**Moving foreward, Step by step…**

* Press start
* Type “windows features”
* Press Enter
* Check the Windows Subsystem for Linux box
* Click OK

* Press Start
* Type “powershell”
* Right click it and click Run as administrator
* Type `Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`
* Press Enter
* Restart.

After the restart….

* Hit Start
* Type “cmd”
* Hit Enter
* Hit Enter In the command prompt after typing `bash`.

This is the way you start the Linux instance. Since it's the first time you've done this, it will start downloading the Ubuntu image from Canonical (which is the non-GUI' user-mode Linux, similar in concept to Windows Server Core). In the future, you can run Linux bash in the future by either of the following ways:

* Type `bash` after opening the command prompt.
* Run the dedicated Bash on Ubuntu on Windows app.

Now, you are ready to go now that you have a nice clean install of Linux, now..

**Install NodeJS**

Installing Node is exactly the same as installing Node on any Linux box in particular, typing these two lines as explained in the [Node Docs](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions):

```
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
sudo apt-get install -y nodejs
```

(Or whatever version you want.)

Now that’s easy, you’ve got Linux and Node already.

**So what is happening here exactly?**

You're [practically in Linux](https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/) as soon as you type `bash` and press in. There is the normal Linux folder structure, but you will find the Windows files mapped to `/mnt` in addition to this. For example, you would find this in `/mnt/c/web/my-project` if you have a project in `C:/web/my-project`. When you switch to Linux, Windows helps you to keep your working directory the same. So you’ll be taken to `/mnt/c/users/david` in Linux, if you’re in the command prompt at `C:\Users\David` and type `bash`.

At first, I found it all bending a bit but it's a best trick better not to think about it.

**You want more?**

There are quite a few Microsoft [blog posts](https://blogs.msdn.microsoft.com/wsl/) about it if you're really curious about how this works under the hood. If you have frequently asked questions and suspect them, go [here](https://msdn.microsoft.com/en-us/commandline/wsl/faq). Check out their [GitHub issues](https://github.com/Microsoft/BashOnWindows/issues), if you have a problem.

**What are some random tips on accessing the command prompt?**

From Explorer with mouse

Hold the shift, right-click and select Open command window here if you are in Explorer looking at your project.

secret-squirrel right click menu

Hit `alt+D` then type `cmd` and hit Enter if you have your project folder opened in Explorer, this shortcut feels pretty weird.
Set the default path for a command prompt

Open a prompt button, then right-click the icon in the taskbar, then right-click Button Prompt (start right-click) and click Properties.

You can then enter a Start in value, which is the prompt to start the directory order.

Pin this icon to the taskbar. Now, the command prompt will open in the proper directory if you click it to open the icon.

You can set this as your default terminal in WebStorm with some [caveats](https://intellij-support.jetbrains.com/hc/en-us/community/posts/207698489-How-can-you-use-new-Bash-on-Ubuntu-on-Windows-terminal-in-Webstorm-).