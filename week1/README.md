# Angular - Week1

> This is the first time we're teaching this new module. Please help us improve it by providing feedback on Slack.

## Reading
Learning Angular means learning to build [web applications](http://angularexpo.com/).

For lesson 1, we'll be understanding every bit of this code snippet.

```
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<h1>Hello {{name}}</h1>`
})
export class AppComponent { name = 'Angular'; }
```

### JavaScript is slowly developed
The first line is something we haven't seen before: the `import` statement.
```
import { Component } from '@angular/core';
```

> Read: [MDN reference on Import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
_estimated time: less than 1 hour (didn't take you that much? slack us!)_

What do you see in the last table? Other than Microsoft Edge, no browser currently supports 'import'. This is one of the biggest challenges of writing JavaScript (or HTML/CSS): making sure that everything we create is supported in every major browser, so that anyone using our code can use it.

Browsers are programs made by different companies. Together they agree on *the* standard of JavaScript. This is currently ES5. `import` is part of a newer standard called 2015. ES2015 is "already" finished today, but it will take time before all companies have implemented ES2015 in their browsers. And by the time ES2015 is implemented, ES7 will already be finished.

> Read (optional): [ES5, ES6, ES2016, ES.Next: What's going on with JavaScript versioning?](https://benmccormick.org/2015/09/14/es5-es6-es2016-es-next-whats-going-on-with-javascript-versioning/)
_estimated time: less than 1 hour (didn't take you that much? slack us!)_

Programmers like us want to use ES2015 today because it makes our code easier to write and to maintain. The `import` statement, for example, is incredibly useful because it allows us to split up our code into smaller files. 

Fortunately we can have the best of both worlds: all of ES2015 and even ES2016 features _today_ while also making sure that everyone can use our application. Solution: the Transpiler! A transpiler "eats up New JavaScript" and "poops out valid old javascript that any browser can understand". The script being pooped out by the Transpiler, let's call it `poop.js` for the convenience, is what we will put into the browser by using it in our HTML file, just like we have been doing so far.

Question for during class: if everything we write in ES2015 can be converted to "old" JavaScript, what does that tell you?

### Our pooper of choice
We'll use Babel. Babel is the most popular transpiler and it runs in Node.js.

> Tutorial: [Get started with Node.js and NPM, make chapters 1-10](https://docs.npmjs.com/getting-started)
_estimated time: 2-6 hours (didn't take you that much? slack us!)_

Before you continue: Make sure you have Node.js version 6.9 or higher and understand how to install an NPM package.

Next, we'll install Babel via NPM.
> Tutorial: [David Walsh tutorial on setup Babel](https://davidwalsh.name/es2015-babel)
_estimated time: 2-4 hours (didn't take you that much? slack us!)_

_Have any issues with these articles? Share your problem on the Slack channel. We can always improve the course material, but need your feedback!_

### Implementing import using Babel
Let's implement `import` and get whatever is pooped out working in our browser.

> Tutorial: How to implement import using Babel.
_estimated time: 2-4 hours (didn't take you that much? slack us!)_





### Line 2: @Component
Most people write their Angular application in TypeScript, and so will we. So far we've learned how to write JavaScript, so we first need a small lesson in TypeScript.

### Getting started with TypeScript

## Exercise - 