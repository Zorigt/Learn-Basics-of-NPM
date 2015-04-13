![Modulus] (https://media.licdn.com/media/p/5/005/083/352/39eb6ec.png)
#Learn The Basics of NPM#
NPM is a great place to get everything you need to build Node.js (node) app. It is a repository for node packages and it's a place where all packages are kept and updated. So, you don't have to constantly check various websites for dependencies and updates. All you need to do is upgrade your packages through NPM by typing npm <option> in command line from your project folder.
##Where to get NPM###
NPM already comes with Node.js when you download and install node on your machine (computer). Try typing `npm --verson` in terminal and it should show something like this.
```node
npm --version
1.4.28
```
It is always good practice to update your npm as it gets updated more frequently than node. So, it is recommended that you get the latest version of npm like so. 
```node
sudo npm install npm -g
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
```
Now, if you check the npm version, it will show that npm updated from 1.4.28 to 2.7.6.
```node
npm --version
2.7.6
```
##Install Packages with NPM##
To most people, the main use of NPM is to install node packages into your project. You're probably familiar with popular packages such as Express, Grunt and Modulus. 
##Installing Packages Locally vs. Globally##
There are two ways to install packages through npm: local and global. Locally installed packages are project specific and normally you use this type of package with `var express = require('express')` in your `app.js` file. On the other hand, global install will create a command line tool such as `grunt`. If you plan to use a package from command line, you'd want to install the package globally. As you read along, you'll learn how to install packages both locally and globally.
##Install Packages Locally##
It is easy to upload packages through npm. Just type `npm install <package>` in command line. This command will install packages locally, which means your packages will be available only within your project scope.
```node
npm install express
npm WARN package.json node@0.0.0 No description
npm WARN package.json node@0.0.0 No repository field.
npm ERR! Darwin 14.0.0
npm ERR! argv "node" "/usr/local/bin/npm" "install" "express"
...
```
If you get a permission error, you may need to type `sudo` in front of `npm`. 
```node
sudo npm install express
Password:
npm WARN package.json node@0.0.0 No description
npm WARN package.json node@0.0.0 No repository field.
express@4.12.3 ../../../node_modules/express
├── merge-descriptors@1.0.0
├── utils-merge@1.0.0
...
```
You can now use `express` package in your project. To test it, just type `express` in your directory and it will create a demo express project. 
```node
express
 create : .
   create : ./package.json
   create : ./app.js
...
```
Here is the best part about using NPM in building apps. As you can see below, `express` package has quite a number of dependencies and some dependency packages are outdated. You can check these by typing `npm ls` and `npm outdated` in command line.
```node
npm ls
1.0.0, required by mod-express@0.0.1
npm ERR! missing: morgan@~1.0.0, required by mod-express@0.0.1
npm ERR! missing: cookie-parser@~1.0.1, required by mod-express@0.0.1
npm ERR! missing: body-parser@~1.0.0, required by mod-express@0.0.1
npm ERR! missing: debug@~0.7.4, required by mod-express@0.0.1
npm ERR! missing: jade@~1.3.0, required by mod-express@0.0.1
...

npm outdated
Package         Current  Wanted       Latest  Location
express         MISSING   4.2.0       4.12.3  express
debug           MISSING   0.7.4        2.1.3  debug
jade            MISSING   1.3.1        1.9.2  jade
body-parser     MISSING   1.0.2       1.12.2  body-parser
static-favicon  MISSING   1.0.2  2.0.0-alpha  static-favicon
cookie-parser   MISSING   1.0.1        1.3.4  cookie-parser
morgan          MISSING   1.0.1        1.5.2  morgan
```
Instead of installing each dependency and doing update individually, you can just type `npm install` and NPM will take care of this tedious task automagically.
```node
npm install

morgan@1.0.1 node_modules/morgan
└── bytes@0.3.0

cookie-parser@1.0.1 node_modules/cookie-parser
├── cookie-signature@1.0.3
└── cookie@0.1.0

body-parser@1.0.2 node_modules/body-parser
├── qs@0.6.6
├── raw-body@1.1.7 (string_decoder@0.10.31, bytes@1.0.0)
└── type-is@1.1.0 (mime@1.2.11)

express@4.2.0 node_modules/express
├── parseurl@1.0.1
├── merge-descriptors@0.0.2
├── utils-merge@1.0.0
...

npm outdated
Package         Current  Wanted       Latest  Location
cookie-parser     1.0.1   1.0.1        1.3.4  cookie-parser
morgan            1.0.1   1.0.1        1.5.2  morgan
static-favicon    1.0.2   1.0.2  2.0.0-alpha  static-favicon
body-parser       1.0.2   1.0.2       1.12.2  body-parser
express           4.2.0   4.2.0       4.12.3  express
debug             0.7.4   0.7.4        2.1.3  debug
jade              1.3.1   1.3.1        1.9.2  jade
```
##Install Packages Globally##
Although it is possible to install all packages globally, the ideal scenario to install a package globally is when you need the package from command line. For example: you would want to use `grunt` as a tool directly from command line. In order to install a package globally, you'd need to add `-g` flag.
```node
npm install -g grunt-cli
```
##Organize Packages with `package.json` File##
When installing a package, you may have noticed a warning message `npm WARN packag.json node@0.0.0 No description`. It is because node uses `package.json` file for configuration and npm also likes to use this file for the same purpose. The good news is that you can just create a file named `package.json` to make the warning go away. It is very easy to create this file. All you have to do is list two parameters `name` and `dependencies` in the json.

The `package.json` file must contain the following.
```javascript
{
  "name": "mod-express",
  
  "dependencies": {
  }
}
```
If you've already created a node project, you'll see `package.json` file is automatically created in your directory. You can edit this json file to add or remove packages directly and call `npm install` from command line to update your project dependencies. You can also use `npm install <package> --save` which will not only install the package but also add the package to `package.json`. This makes it easy for node app to be cloned and collaborate with team of developers. 

An example of `package.json` file created by Express.js looks like this.
```node
{
  "name": "mod-express",
  "version": "0.0.1",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "express": "~4.2.0",
    "static-favicon": "~1.0.0",
    "morgan": "~1.0.0",
    "cookie-parser": "~1.0.1",
    "body-parser": "~1.0.0",
    "debug": "~0.7.4",
    "jade": "~1.3.0"
  }
}
```
