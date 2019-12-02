---
title: How to uninstall npm modules in node js?
image: "/assets/default-social-image.png"
categories: Npm
---

As commonly known, any npm module can be installed by running a simple command: `npm install <module_name>`.

I have installed a few modules that I do not use anymore and I just want to get them off. I have a few questions regarding this:

* Do we have any command or process to uninstall a module from the root (something like `npm uninstall <module_name>`) or will simply removing the module files do?
* How does it affect us if we keep the unused modules?

**#1.** The command is simply `npm uninstall <name>`

The nodejs documents [https://npmjs.org/doc/](https://npmjs.org/doc/) have all the commands that you need to know with npm.

A local install will be in the `node_modules/` directory of your application. This won't affect the application if a module remains there with no references to it.

If you're removing a global package however, any applications referencing it will crash.

Here are different options:

`npm uninstall <name>` removes the module from `node_modules`, but not `package.json`

`npm uninstall <name>` --save also removes it from `dependencies` in `package.json`

`npm uninstall <name>` --save-dev also removes it from `devDependencies` in `package.json`

`npm -g uninstall <name>` --save also removes it globally

**#2.** If it doesn't work with `npm uninstall <module_name>` try it globally by typing `-g`.

Maybe you just need to do it as an superUser/administrator with `sudo npm uninstall <module_name>`.

**#3.** Well to give a complete answer to this question, there are [two methods](https://docs.npmjs.com/getting-started/uninstalling-local-packages): (for example we call the installed module as module1)

1. To remove module1 without changing package.json: `npm uninstall module1`
2. To remove module1 with changing package.json, and removing it from the dependencies in package.json: `npm uninstall --save module1`

Note: to simplify the above mentioned commands, you can use **-S** instead of **--save** , and can use **remove**, **rm**, **r**, **un**, **unlink** instead of **uninstall**

**#4.** I just install stylus by default under my home dir, so I just use `npm uninstall stylus` to detach it, or you can try `npm rm <package_name>` out.

**#5.** To uninstall the node module:

`npm uninstall <module_name>  `

This will remove the module from node_modules, but not from package.json. So when we do npm install again it will download the module.

So to remove the module from package.json use:

`npm uninstall <module_name> --save  `

This also delete the dependency from package.json.

And if you want to uninstall any globally module you can use:

`npm -g uninstall <module_name> --save `

This will delete the dependency globally.

**#6.** To remove packages in `node_modules/` in bulk, you could also remove them from `package.json`, save it, and then run `npm prune` on the terminal.

This will remove those packages, which exist in the filesystem, but are not used/declared `package.json`.

P.S> This is particularly useful on Windows, as you may often encounter problems with being unable to delete some files due to the "exceeded path length limit".

**#7.** I found this out the hard way, even if it is seemingly obvious.

I initially tried to loop through the node_modules directory running `npm uninstall module-name` with a simple for loop in a script. I found out it will not work if you call the full path, e.g

`npm uninstall module-name`

was working, but

`npm uninstall /full/path/to/node_modules/module-name `

was not working.

**#8.** For Windows Users - If you want to remove all the node modules installed at once:

1. Open powershell
2. Go inside node_modules folder (cd node_modules)
3. Run this command - "npm uninstall (Get-ChildItem).Name"

It will uninstall all the modules.

**#9.** The `uninstall` option didn't work for me when I tried to use the same command to the one I used in installing (as I was installing with the `@latest` directive)

So for example, I installed a package like this:

`npm install  @ngtools/webpack@latest`

And then I wanted to uninstall it so I used the same command (including @latest)

`npm uninstall  @ngtools/webpack@latest`

So the above uninstall didn't work, I have to remove the @latest & then it worked well

`npm uninstall  @ngtools/webpack`

I hope this helps

**#10.** Sometimes `npm uninstall -g packageName` doens't work.

In this case you can delete package manually.

On Mac go to folder `/usr/local/lib/node_modules` and delete folder with package you want. That's it. Check your list of globally installed packages with this command `npm list -g --depth=0`

**#11.** Update npm 5:

As of [npm 5.0.0](https://blog.npmjs.org/post/161081169345/v500), installed/uninstalled modules are added/removed as a dependency by default, so the --save option is no longer needed.

run

`npm uninstall <package>`

for example:

`npm uninstall mongodb`

It will remove the module from node_modules folder and package.json file also

**#12.** You can also run the following as shorthand:

`npm un packageName` or `npm rm packageName`

Note: Add `-g` at end of command to uninstall global packages.

**#13.** 

```
# login as root (might be required depending on install)
su - 
# list all global packages
npm ls -g --depth=0
# list all local (project) packages
npm ls -p --depth=0
# remove all global packages
npm ls -g --depth=0 | awk -F/ '/node_modules/ && !/\/npm$/ {print $NF}' | xargs npm -g rm
# remove all local packges
npm ls -p --depth=0 | awk -F/ '/node_modules/ && !/\/npm$/ {print $NF}' | xargs npm -p rm

# NOTE (optional): to use node with sudo you can add the bins to /usr/bin
# NOTE $PATHTONODEINSTALL is where node is installed (e.g. /usr/local/node)
sudo ln -s $PATHTONODEINSTALL/bin/node /usr/bin/node
sudo ln -s $PATHTONODEINSTALL/bin/npm /usr/bin/npm
```

**#14.** Use `npm uninstall <packageName> --save` to uninstall a package and remove it's entry in `package.json`.

`npm uninstall -g <packageName> --save` will uninstall the package if it was added globally.

**#15.** To uninstall a module using npm, you can use:

`npm uninstall moduleName`

Also, if you want to uninstall and want the change to be reflected in your package.json then you can use the --save flag, like this:

```
npm uninstall moduleName --save
OR
npm uninstall -S
```

And if you want to uninstall a module from devDependencies and want the change to be reflected in package.json then you can use -D flag, like this:

`npm uninstall moduleName -D`

**#16.** You can uninstall the node modules in the following ways

1. Uninstall the package: npm uninstall `<Package Name>`
2. Uninstall the package and remove it from dependencies in package.json: npm uninstall `<Package Name> --save`
3. Uninstall the package and remove it from dev dependencies in package.json: npm uninstall `<Package Name> --save-dev`
4. Uninstall a global package. Global packages can be accessed anywhere throughout the system, not limited to a specific project: `npm uninstall -g <Package Name>`