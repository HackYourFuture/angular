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

### Line 1: import
Read the following article on import.

> Read: [MDN reference on import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

What do you see in the last table? Other than Microsoft Edge, no browser currently supports 'import'. This is one of the biggest challenges of writing JavaScript (or HTML/CSS): making sure that everything we create is supported in every major browser, so that anyone using our code can use it.

Browsers are programs made by different companies. Together they agree on *the* standard of JavaScript. This is currently ES5. ES2015 is already finished, but it will take many months until all companies have put ES2015 into their browsers. And by the time ES2015 is implemented, ES7 will already be finished.

Programmers like us want to use ES2015 today, because it makes our code easier to write and to maintain. The `import` statement, for example, is incredibly useful because it allows us to split up our code into smaller files. 

Fortunately we can have the best of both worlds: all of ES2015 and even ES7 features _today_ while also making sure that everyone can use our application. The Transpiler! We'll use Babel. Babel runs in Node.js.

> Tutorial: [Get started with Node.js and NPM, chapters 1-10](https://docs.npmjs.com/getting-started)? 

Before you continue: Make sure you have Node.js version 6.9 or higher and understand how to install an NPM package.

Next, we'll install Babel as NPM.
> Tutorial: [David Walsh tutorial on setup Babel](https://davidwalsh.name/es2015-babel)

Have any issues with these articles? Share your problem on the Slack channel. We can always improve the course material, but need your feedback!

Let's implement `import`.




### Line 2: @Component
Most people write their Angular application in TypeScript, and so will we. So far we've learned how to write JavaScript, so we first need a small lesson in TypeScript.

### Getting started with TypeScript

## Exercise - 