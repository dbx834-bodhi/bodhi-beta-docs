# Introduction

This document has been inspired by [this article](http://guide.meteor.com/code-style.html) by Meteor. It is an extension of the document for Bodhi code.

## Benefits of consistent style

"Countless hours have been spent by developers throughout the years arguing over single vs. double quotes, where to put brackets, how many spaces to type, and all kinds of other cosmetic code style questions. These are all questions that have at best a tangential relationship to code quality, but are very easy to have opinions about because they are so visual."

"While it’s not necessarily important whether your code base uses single or double quotes for string literals, there are huge benefits to making that decision once and having it be consistent across your organization. These benefits also apply to the Meteor and JavaScript development communities as a whole."

-- from [Code Style by Meteor](http://guide.meteor.com/code-style.html)

## Before proceeding

* Please read the [Code Style by Meteor](http://guide.meteor.com/code-style.html) before proceeding
* [Install ESLint](http://guide.meteor.com/code-style.html#eslint-installing)
* [Integrate ESLint with your editor](http://guide.meteor.com/code-style.html#eslint-editor)

## Javascript Code Style

We will follow the [Airbnb style guide](https://github.com/airbnb/javascript) for our javascript

## Meteor Specific Code Style

### Database: Collections

> ```javascript
> // Defining a collection
> Lists = new Mongo.Collection('Lists');
> ```

* Collections should be named as a **plural noun**, in **PascalCase**.
* The name of the collection in the database should be the same as the name of the JavaScript symbol.
* Fields in the collection should be camelCased (just like JavaScript variable names).

