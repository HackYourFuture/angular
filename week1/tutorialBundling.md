# Using a bundler: Webpack
In this tutorial we will learn:
- How and when to use [Webpack](https://webpack.js.org/)
- Combine multiple ES6 modules into one file using Webpack and Babel
- Deploy our code on a webpage

> For this tutorial, we presume you know all about Node, NPM and Babel as outlined in [this tutorial]()

### Babel recap
Building on the previous tutorial on Babel, we should have the following file structure:

```
-babel-in-action/
---node_modules/
---package.json
---dist/
-----index.js
---src/
-----index.js
```

```
// package.json
{
  "name": "babel-in-action",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "babel-cli": "^6.23.0",
    "babel-preset-env": "^1.1.8"
  },
  "babel": {
    "presets": ["env"]
  }
}
```

### Why do we split up files?
There is no hard answer to this, but a couple of soft answers:
- Like a book has chapters - A program has modules
- When we use libraries like jQuery or Angular, it's much easier to install new versions or uninstall
- Big files are much more difficult to maintain than small files. This is called Separation of Concern (SoC) - and a very important aspect of writing good code.

> Read: [Seperation of Concerns](http://deviq.com/separation-of-concerns/)

> Read: [Single Responsibility Principle](http://deviq.com/single-responsibility-principle/)

### Splitting up our code.
We're going to make a very simple application that does some math operations and seperate our concerns in to two files. When a file is dedicated to a specific goal, we can call it a Module, though there is no hard distinction.

Add two files to folder `src/`: `multiply.js` and `subtract.js` with the following content.
```
// src/multiply.js
function multiply(arg1, arg2) {
	return arg1 * arg2;
}
```

```
// src/subtract.js
function subtract(arg1, arg2) {
	return arg1 - arg2;
}
```

To use these two functions in `src/index.js` we do the following.
```
// src/index.js

import { subtract } from './subtract';
import { multiply } from './multiply';

var a = 5;
var b = 10;

var c = multiply(a, b);
var d = subtract(a, b);

document.getElementById('result1').innerHTML = c;
document.getElementById('result2').innerHTML = d;
```

Let's also add `index.js` to an html file and start using it in our web browser.
```
// src/index.html
<html>
  <head>
  	<title>Using modules in html</title>
  </head>
  <body>
    <div>And the first result is... <span id="result1"></span></div>
    <div>And the second result is... <span id="result2"></span></div>
    <script src="index.js"></script>
  </body>
</html>
```

When we open `index.html` in Chrome or Firefox, we get the following error:
```
Uncaught SyntaxError: Unexpected token import
```

Transpiling the code using Babel results in `import` being transpiled to `require`. Unfortunately, this, too, is not implemented in any browser. The reason is because there _is_ no way to import modules using just JavaScript. Even Babel doesn't help us with importing modules, because it's such a specific thing.

So we use Webpack: a tool that is made specifically for combining modules and making them ready to distribute in web browsers.

### Installing Webpack
First, we install Webpack locally using NPM
```
npm install --save-dev webpack
```

Next, we use webpack just like we used Babel, with a `src` and a `dist`. However, we must first transpile, than bundle the result into one file.

So the flow looks like
```
src/index.js + src/multiply.js + src/subtract.js
==TRANSPILE==>
dist/index.js + dist/multiply.js + dist/subtract.js
==BUNDLE==>
dist/bundle.js
```

To achieve this we run webpack:
```
./node_modules/.bin/babel src -d dist
./node_modules/.bin/webpack dist/index.js dist/bundle.js
```

The result is a new file `dist/bundle.js` that contains a little over 100 lines, and includes our modules `multiply` and `subtract`.

Next, copy and paste `src/index.html` to a new file `dist/index.html` and change `index.js` to `bundle.js`

```
// dist/index.html
<html>
  <head>
  	<title>Using modules in html</title>
  </head>
  <body>
    <div>And the first result is... <span id="result1"></span></div>
    <div>And the second result is... <span id="result2"></span></div>
    <script src="bundle.js"></script>
  </body>
</html>
```

Opening this file in Chrome should leave you with a working file!

### Summary
We started this tutorial with the poop coming out of Babel. This is valid ES5, *except for the import statement*. Because importing modules is like chocolate, so essential, we installed Webpack to do the importing for us. So Webpack eats what eats Babel poops, and Webpack in turn poops out TRULY web-ready ES5 code.

### Next tutorial
We now have an annoying issue. If we want to update our ES6 code, we have to run two commands (babel and then webpack) before we can test this in our browser. Fortunately, we can automate this process. We're gonna build something that does this: every time we save the file, our transpiling + bundling pipeline runs automatically. 

