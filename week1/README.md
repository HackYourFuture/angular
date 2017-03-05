# HackYourFuture Angular - Reading material week 1

> This is the first time we're teaching this new module. Please help us improve it by providing feedback on Slack.

Learning Angular means learning to build [web applications like these](http://angularexpo.com/). Many companies use Angular, so learning it might give us some job opportunities!

For lesson 1, we're going to study every bit of this code snippet. 

```
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<h1>Hello {{name}}</h1>`
})
export class AppComponent { name = 'Angular'; }
```

To understand this code snippet, we'll have to start by looking at two JavaScript supersets: ES6 and TypeScript. When we understand this, we can start looking at Angular itself and make our first application.

### Line 1: JavaScript is slowly implemented
The first line is something we probably haven't seen before: the `import` statement.
```
import { Component } from '@angular/core';
```

Checkout the Browser compatibility table in [this MDN reference on import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import). What do you see? Other than Microsoft Edge, no browser currently supports the use of `import`. Here we see one of the biggest challenges of writing JavaScript (or HTML/CSS) for the web: making sure that everything we create is supported in every major browser, so that anyone loading our code in their browser can use it.

Browsers are programs made by different companies. Together they agree on *the* standard of JavaScript. This is currently ES5. `import` and [many other awesome features](http://es6-features.org/) is part of a newer standard called ES6 (officially called ES2015). ES6 is "already" finished today, but it will take time (we don't know when) before all companies have implemented ES6 in their browsers. And by the time ES6 is implemented across the board, ES7 will be out with useful features.

> Read (optional): [awesome website covering all ES6 features and how they are converted to ES5](http://es6-features.org/) _estimated time: as long as you like_

> Read (optional): [ES5, ES6, ES2016, ES.Next: What's going on with JavaScript versioning?](https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning/) _estimated time: less than 1 hour_

Programmers like us want to use ES6 today because it makes our code easier to write and to maintain. The `import` statement, for example, is incredibly useful. It allows us to split up our code into smaller files and makes it easy to use code others have written. In the above example we import part of Angular and make it ours!

Fortunately we can have the best of both worlds: all of ES6 (and even ES7) features _today_ while also making sure that everyone can safely use our applications. Introducing: the Transpiler and the Bundler! In short, a transpiler and bundler "eat up New JavaScript" and "poop out valid old javascript that any browser can understand". The script being pooped out by these two, let's call it `poop.js` for convenience sake, is what we will put into the browser by using it in our HTML file, just like we have been doing so far.

### Our poopers of choice
We'll use Babel. Babel is the most popular transpiler and it runs in Node.js.

> Tutorial: [Get started with Node.js and NPM, make chapters 1-10](https://docs.npmjs.com/getting-started)
_estimated time: 2-6 hours_

Before you continue: Make sure you have Node.js version 6.9 or higher and understand how to install an NPM package.

Let's start with a tutorial on how to use Babel to convert ES6+ to ES5.
> Tutorial: [using Babel to transpile](tutorialTranspiling.md) _estimated time: 2-4 hours_

Then, we also need to use a bundler. Why and how will be explained in the tutorial.
> Tutorial: [using Webpack to bundle](tutorialBundling.md) _estimated time: 2-4 hours_

Before proceeding to TypeScript, let's learn about an ES6 feature that's essential for Angular: classes
> Tutorial [ES6 Classes introduction (Dan Wahlin)](https://weblogs.asp.net/dwahlin/getting-started-with-es6-using-classes) _estimated time: 1-4 hours_

> Tutorial (optional, this is a biggy) [ES6 Classes deep dive (scotch.io)](https://scotch.io/tutorials/better-javascript-with-es6-pt-ii-a-deep-dive-into-classes) _estimated time: more than 6 hours_

Then, with ES6 classes in the back of our minds
> Tutorial [Typescript](tutorialTypescript.md) _estimated time: 2-6 hours_

_Have any issues with these articles or did you find a better tutorial onlien? Share your knowledge on the Slack channel!_

### Reflective questions for Class 1:
- If everything we write in ES6 can be converted to "old" JavaScript, what does that tell us about ES6?
- What's the importance of Transpiling code?
- Why do we use a Bundler?
- What is Node.js?
- What is SoC and why is it important?
- What is a Class and why is it useful?
- What is TypeScript and why do we use it?

### Additional reading
Why not to use frameworks (as Michael puts it: stay open to critique on your methods. Keeps you sharp)
- [Why I hate Frameworks by Bunch of guys](http://discuss.joelonsoftware.com/default.asp?joel.3.219431.12)
- [Why libraries are better than frameworks, Tom Lokhorst](http://tom.lokhorst.eu/2010/09/why-libraries-are-better-than-frameworks)

- [ToddMotto: TypeScript, the missing introduction](https://toddmotto.com/typescript-the-missing-introduction)
