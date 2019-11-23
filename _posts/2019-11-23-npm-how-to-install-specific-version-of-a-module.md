---
image: "/assets/default-social-image.png"
categories: Npm
title: 'NPM: How to Install Specific Version of a Module'
---

Node and NPM beginners often question how to download and install some different NPM package version which can be accomplished in several ways but first, let's start with the basic syntax of the NPM CLI:

`npm install lodash`
 
This command downloads `lodash` and gets the latest version available in the current directory.

Note: If you know the exact package version, then after the @ character you can add it to the package name:

`npm install lodash@4.17.4`
 
For any NPM kit, you can check the latest version at [npmjs.com](https://www.npmjs.com/package/lodash).

NPM will allow you to define the version using semant ranges if you don't know the exact version of the package. For example,

`npm install lodash@^4.0.0`
 
More about the semantic versioning syntax can be found at [docs.npmjs.com](https://docs.npmjs.com/getting-started/semantic-versioning) and by this command, the new 4.x.x update will be downloaded and installed by this order. 

Both of the above examples do not add installed modules to the dependency list and do not change the.json package. Use `--save` and add the module installed to devDependencies with `--save-dev` after adding the enabled module to the dependencies of the package.json. NPM will add the semantic range to the.json package as it is if you install a module without a specific version or semantic range. Use `--save-exact` flag as well as `--save` or `--save-dev` to prevent it which will force NPM in the package.json to store the exact version of the module.

Examples

1. npm install lodash --save --save-exact - Saves the exact version in the.json package dependencies after it installs the latest release. 
2. npm install lodash --save-dev --save-exact - Saves the exact version of the.json package in the devDependencies map and installs the latest release.
3. npm install lodash --save - Saves the weekly array in the.json package dependencies and installs the latest release, like the "lodash":"^4.17.4" as an example.

Caveats

1. It is not sufficient to mention `--save-exact` alone. You have to describe `--save` or `--save-dev` and `--save-exact`. Like `npm install mocha --save-dev --save-exact` or `npm install lodash --save --save-exact`, as example.
2. Clearly, the `-g` flag that installs the module globally does not operate with `--save`, `--save-exact`, `--save-dev`.

You can buy [this book](https://www.amazon.com/gp/product/1785885588/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1785885588&linkCode=as2&tag=orkon-20&linkId=5324845d5b784fea07d15439f5f6e88d) if you are learning Node.js.