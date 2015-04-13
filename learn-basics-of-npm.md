![Modulus] (https://media.licdn.com/media/p/5/005/083/352/39eb6ec.png)
#Learn The Basics of NPM#
NPM is a great place to get everything you need to build Node.js app. It is a repository for Node packages and it's a place where all packages are kept and updated. So, you don't have to constantly check various websites for depencecy updates. All you need to is upgrade your packages through NPM by typing `npm <option>` in command line from your project folder. 

##Where to get NPM?###
NPM already comes with Node.js when you download and install Node on your machine (computer). Try typing `npm --verson` terminal and it should show something like this.
```
npm --version
1.4.28
```
It is always good practice to update your npm as npm gets updated more frequently than node. So, it is recommended that you get the latest version of npm like so. 
```
sudo npm install npm -g
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
```
Now, if you check the updated npm version, it will show that npm upgraded from 1.4.28 to 2.7.6.
```
npm --version
2.7.6
```
##Install Packages with NPM##
To most people, the main use of NPM is to install node packages into your project. You're probably familiar with popular packages such as Express.js, Angular.js and Modulus. It is easy to upload packages through npm. Just type `npm install <package>` in command line. If you get a permission error, you may need to type `sudo` infront of npm. 
```
npm install express
npm WARN package.json node@0.0.0 No description
npm WARN package.json node@0.0.0 No repository field.
npm ERR! Darwin 14.0.0
npm ERR! argv "node" "/usr/local/bin/npm" "install" "express"
npm ERR! node v0.10.33
npm ERR! npm  v2.7.6
```
If you get a permission error, you may need to type `sudo` infront of `npm`. 
```
sudo npm install express
Password:
npm WARN package.json node@0.0.0 No description
npm WARN package.json node@0.0.0 No repository field.
express@4.12.3 ../../../node_modules/express
├── merge-descriptors@1.0.0
├── utils-merge@1.0.0

```
You may have noticed a warning message `npm WARN packag.json node@0.0.0 No description` and it is because node uses `package.json` file as configuration. Therefore, npm also likes to use this file for same purpose. The good news is that you can just create and the warning will go away. It is easy to create the file and all you need to do is list two parameters `name` and `dependencies`. 
```javascript
{
  "name": "mod-express"
  },
  "dependencies": {
  }
}
```

##Install Locally##

##Install Globally##

##Installing Locally vs. Globally##

