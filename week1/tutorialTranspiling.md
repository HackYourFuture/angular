# Using a Transpiler: Babel
In this tutorial we will learn:
- Install [Babel](https://babeljs.io/)
- Write valid [ES6](https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning/)
- Use Babel to transpile our valid ES6 to valid ES5 that we can safely run in every modern browser.

> For this tutorial, we presume you are up and running with [Node.js](https://docs.npmjs.com/getting-started)


### Create new project
Let's create a new NPM project. If this is new to you, first do the above tutorial.

```
mkdir babel-in-action
cd babel-in-action
npm init
```

Now, my folder structure looks like this:
```
-babel-in-action/
---package.json
```

### Installing Babel locally
We'll install Babel locally, because this makes is easier later share our work.
```
npm install --save-dev babel-cli
```

_Note: we use the `--save-dev` instead of `--save`. For this example, it won't make a difference. But it's good practice to start doing this right now. Think of it this way: everything you install with `--save` is code that you will need in your end product. For example we might install Angular or jQuery using the `--save` flag. Babel (and other development tools like Jasmine) are simply used in the development process. It's not shipped in the code itself. That's when you use `--save-dev`. Later, when we're going to use tools like WebPack or System.JS this makes a difference._

Next, we need to "teach" babel how to eat ES6 and poop out ES5.
```
npm install --save-dev babel-preset-env
```

After this, your folder should look like this
```
-babel-in-action/
---node_modules/
---package.json
```

and your `package.json` like this:
```
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
  }
}
```

Now we can run Babel from our command line. The location of the babel program is `./node_modules/.bin/babel`. That's it, we're completely ready to write modern ES6! Let's give this a go.

### Transpiling ES6 to ES5
We create two new folders inside our project:
- `src/`: short for source - will contain all of our ES6 files
- `dist/`: short for distribution - will contain all of our ES5 files that are safe to use in a browser

```
mkdir src
mkdir dist
```

Inside `src/` we create a new file called `index.js`. Result:
```
-babel-in-action/
---node_modules/
---package.json
---dist/
---src/
-----index.js
```

Let's write some simple ES5 in `src/index.js`.

```
// src/index.js
var x = [1, 2, 3, 4, 5];
var y = x.map(function(element) {
	return element + 10;
});
console.log(y);
```

> Read: [MDN on .map()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

In our command line, we call the babel program and tell it to eat our `src` folder and poop out the result to the `dist` folder. For some reason, the babel authors write poop with a d, so the result is the -d flag. Which really stands for pooping.

```
./node_modules/.bin/babel src -d dist
```

Open the dist folder and see what happened! If all went well, babel created `index.js` in your `dist` folder. 

Next stop: ES6.

Let's write an [arrow function](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions) in `src/index.js`.

```
// src/index.js
var x = [1, 2, 3, 4, 5];
var y = x.map(element => element + 10);
console.log(y);
```

Again, call babel
```
./node_modules/.bin/babel src -d dist
```

Take a look at `dist/index.js`. What do you see? The exact same thing as in `src/index.js`! Why isn't Babel transpiling ES6 to ES5? Because we haven't told it to. This is how babel looks for config.

> Babel will look for a .babelrc in the current directory of the file being transpiled. If one does not exist, it will travel up the directory tree until it finds either a .babelrc, or a package.json with a "babel": {} hash within.

Why add another file if we don't have to? Let's open up `package.json`. Here, we will tell babel to use the `env` plugin we installed earlier this tutorial.

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

Now run babel again.
```
./node_modules/.bin/babel src -d dist
```

Should look like this:
```
"use strict";

// src/index.js
var x = [1, 2, 3, 4, 5];
var y = x.map(function (element) {
  return element + 10;
});
console.log(y);
```

Magic!!! We've successfully transpiled ES6 to ES5.


### What's next?
Now we can use ALMOST all ES6 and ES7 features in our code, meaning that we can use new features in our code and Babel will make sure it is transpiled to browser safe-code.

There is, however, one essential thing that is still missing even with babel: combining multiple files. In HTML, we can include multiple javascript files, like so:
```
<html>
  <head>
    <script src="library/jquery.js"></script>
    <script src="library/underscore.js"></script>
    <script src="library/someotherlibrary.js"></script>
  </head>
  <body>
    <script src="app/index.js"></script>
  </body>
</html>
```

However, this makes for very difficult developing. If you're writing a javascript function in index.js, how can you be sure that jquery and underscore is being loaded in the same html file, and _before_ your JavaScript needs it.

So, in another tutorial, we will take a look at how we can safely load files into our JavaScript. 

> Recommended next reading: tutorialBabel




