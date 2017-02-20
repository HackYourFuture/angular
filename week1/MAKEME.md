# Angular - Reading material for week 1

> This is the first time we're teaching this new module. Please help us improve it by providing feedback on Slack.

Our first Angular product is going to be, of course, a working web-applicationt that fully implements the Model View Controller (MVC) pattern.

That means we're going to have, in our application:
 - A Model (a piece of data)
 - A View (a HTML template that shows the data to the user and let's the user give input)
 - A Controller (a piece of code that knows what to do with user input and perform some logic)

## How to hand in the assignment
To streamline the homework process, we've already initiated a repo on github. This is *only* the product of `ng new xxx`. Before cloning, give the `ng new` command a shot. There's nothing to it. Why already make this repo instead of letting everyone do `ng new` and push themselves? Well, we're going to check homework from now on through pull requests. If we all contribute to 1 repo, it's super easy to see exactly what someone did _other than `ng new`_ because `ng new` will create 10.000 lines. And working through 10.000 lines to find 10 that someone made is quite bother.

### Before you start
1) `cd` to the folder you make all your homework.
2) Go to [this repo](https://github.com/HackYourFuture/angular-class7)
3) Click "fork" in the top right, fork it under your personal github account
4) Clone this new repo to your homework folder on your computer
5) Run `npm install`
6) You're good to go!

### When you are done
1) Commit and Push your changes
2) Go to your personal fork of the repo in github
3) Here, it will say "1 commit ahead of hackyourfuture/angular-class7/master". Then it says "create pull request"
4) Create a pull request
5) That's it!

## Assignment Requirements
Software requirements:
- We Use at Angular 2 written in TypeScript
- You may include any other library/package

Functional requirements:
- As a user I want to view my list of X
- As a user I want to add a new item to my list of X
- As a user I want to edit existing items in my list of X
- As a user I want to delete existing items from my list of X

Technical requirements:
- The model needs to be strongly typed
- At least two components