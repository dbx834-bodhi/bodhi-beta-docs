# Introduction

This document has been inspired by [this article](http://guide.meteor.com/code-style.html) by Meteor.

## Benefits of Consistent Style

"Countless hours have been spent by developers throughout the years arguing over single vs. double quotes, where to put brackets, how many spaces to type, and all kinds of other cosmetic code style questions. These are all questions that have at best a tangential relationship to code quality, but are very easy to have opinions about because they are so visual."

"While it’s not necessarily important whether your code base uses single or double quotes for string literals, there are huge benefits to making that decision once and having it be consistent across your organization. These benefits also apply to the Meteor and JavaScript development communities as a whole."

-- from [Code Style by Meteor](http://guide.meteor.com/code-style.html)

## Before Proceeding

* Please read the [Code Style by Meteor](http://guide.meteor.com/code-style.html) before proceeding
* [Install ESLint](http://guide.meteor.com/code-style.html#eslint-installing)
* [Integrate ESLint with your editor](http://guide.meteor.com/code-style.html#eslint-editor)

## Javascript Code Style

We will follow the [Airbnb JS style guide](https://github.com/airbnb/javascript) for our JS

## Meteor Specific Code Style

> ```javascript
> // Demo: 2.1, 2.2
> // Methods are camelCased and namespaced to the module they belong to
>
> // in imports/api/todos/methods.js
> updateText = new ValidatedMethod({
>   name: 'todos.updateText',
>   // ...
> });
> ```

> ```javascript
> // Demo: 3.3
> // If you have a file that exports a class
> export default class ClickCounter { ... }
> // This class should be defined inside a file called ClickCounter.js.
> ```

> ```javascript
> // When you import it, it’ll look like this
> import ClickCounter from './ClickCounter.js';
> // Note that imports use relative paths, and include the file extension at the end of the file name.
> ```

1. [Meteor guide on Collections](http://guide.meteor.com/code-style.html#collections)
2. [Meteor guide on Methods](http://guide.meteor.com/code-style.html#methods-and-publications)
  1. Method names should be camelCased
  2. Method names should be namespaced to the module they are in
3. [Meteor guide on Files, exports, and packages](http://guide.meteor.com/code-style.html#files-and-exports)
  1. Each file in the app should represent one logical module
  2. Avoid having catch-all utility modules that export a variety of unrelated functions and symbols
  3. The file should be named the same as the thing it defines, with the same capitalization


## React Template Code Style

We will follow the [Airbnb react style guide](https://github.com/airbnb/javascript/tree/master/react) for JSX

> ```javascript
> // Demo: 3
> // bad
> const Listing = React.createClass({
>   // ...
>   render() {
>     return <div>{this.state.hello}</div>;
>   }
> });
> 
> // good
> class Listing extends React.Component {
>   // ...
>   render() {
>     return <div>{this.state.hello}</div>;
>   }
> }
> ```

> ```javascript
> // Demo: 4
> // bad
> class Listing extends React.Component {
>   render() {
>     return <div>{this.props.hello}</div>;
>   }
> }
> 
> // bad
> const Listing = ({ hello }) => (
>   <div>{hello}</div>
> );
> 
> // good
> function Listing({ hello }) {
>   return <div>{hello}</div>;
> }
> ```

> ```javascript
> // Demo: 5.3
> // bad
> import reservationCard from './ReservationCard';
> 
> // good
> import ReservationCard from './ReservationCard';
> 
> // bad
> const ReservationItem = <ReservationCard />;
> 
> // good
> const reservationItem = <ReservationCard />;
> ```

> ```javascript
> // Demo: 6
> // bad
> export default React.createClass({
>   displayName: 'ReservationCard',
>   // stuff goes here
> });
> 
> // good
> export default class ReservationCard extends React.Component {
> }
> ```

> ```javascript
> // Demo: 7
> // bad
> <Foo superLongParam="bar"
>      anotherSuperLongParam="baz" />
> 
> // good
> <Foo
>   superLongParam="bar"
>   anotherSuperLongParam="baz"
> />
> 
> // if props fit in one line then keep it on the same line
> <Foo bar="bar" />
> 
> // children get indented normally
> <Foo
>   superLongParam="bar"
>   anotherSuperLongParam="baz"
> >
>   <Quux />
> </Foo>
> ```

> ```javascript
> // Demo: 8.1, 8.2
> // bad
> <Foo bar='bar' />
> 
> // good
> <Foo bar="bar" />
> 
> // bad
> <Foo style={{ left: "20px" }} />
> 
> // good
> <Foo style={{ left: '20px' }} />
> ```

> ```javascript
> // Demo: 9.1, 9.2
> // bad
> <Foo/>
> 
> // very bad
> <Foo                 />
> 
> // bad
> <Foo
>  />
> 
> // good
> <Foo />
> 
> // bad
> <Foo bar={ baz } />
> 
> // good
> <Foo bar={baz} />
> ```

> ```javascript
> // Demo: 10.1
> // bad
> <Foo
>   UserName="hello"
>   phone_number={12345678}
> />
> 
> // good
> <Foo
>   userName="hello"
>   phoneNumber={12345678}
> />
> ```

> ```javascript
> // Demo: 10.2
> // bad
> <Foo
>   hidden={true}
> />
> 
> // good
> <Foo
>   hidden
> />
> ```

> ```javascript
> // Demo: 10.3
> // bad
> <img src="hello.jpg" />
> 
> // good
> <img src="hello.jpg" alt="Me waving hello" />
> 
> // good
> <img src="hello.jpg" alt="" />
> 
> // good
> <img src="hello.jpg" role="presentation" />
>
> // bad
> <img src="hello.jpg" alt="Picture of me waving hello" />
> 
> // good
> <img src="hello.jpg" alt="Me waving hello" />
> ```

> ```javascript
> // Demo: 10.4
> // bad - not an ARIA role
> <div role="datepicker" />
> 
> // bad - abstract ARIA role
> <div role="range" />
> 
> // good
> <div role="button" />
> ```

> ```javascript
> // Demo: 10.5
> // bad
> <div accessKey="h" />
> 
> // good
> <div />
> ```

> ```javascript
> // Demo: 10.6
> // bad
> {todos.map((todo, index) =>
>   <Todo
>     {...todo}
>     key={index}
>   />
> )}
> 
> // good
> {todos.map((todo) =>
>   <Todo
>     {...todo}
>     key={todo.id}
>   />
> )}
> ```

> ```javascript
> // Demo: 11.1
> // bad
> render() {
>   return <MyComponent className="long body" foo="bar">
>            <MyChild />
>          </MyComponent>;
> }
> 
> // good
> render() {
>   return (
>     <MyComponent className="long body" foo="bar">
>       <MyChild />
>     </MyComponent>
>   );
> }
> 
> // good, when single line
> render() {
>   const body = <div>hello</div>;
>   return <MyComponent>{body}</MyComponent>;
> }
> ```

> ```javascript
> // Demo: 12.1, 12.2
> // bad
> <Foo className="stuff"></Foo>
> 
> // good
> <Foo className="stuff" />
> 
> // bad
> <Foo
>   bar="bar"
>   baz="baz" />
> 
> // good
> <Foo
>   bar="bar"
>   baz="baz"
> />
> ```

> ```javascript
> // Demo: 13.1
> function ItemList(props) {
>   return (
>     <ul>
>       {props.items.map((item, index) => (
>         <Item
>           key={item.key}
>           onClick={() => doSomethingWith(item.name, index)}
>         />
>       ))}
>     </ul>
>   );
> }
> ```

> ```javascript
> // Demo: 13.2
> // bad
> class extends React.Component {
>   onClickDiv() {
>     // do stuff
>   }
>
>   render() {
>     return <div onClick={this.onClickDiv.bind(this)} />
>   }
> }
>
> // good
> class extends React.Component {
>   constructor(props) {
>     super(props);
>
>     this.onClickDiv = this.onClickDiv.bind(this);
>   }
>
>   onClickDiv() {
>     // do stuff
>   }
>
>   render() {
>     return <div onClick={this.onClickDiv} />
>   }
> }
> ```

> ```javascript
> // Demo: 13.3
> // bad
> React.createClass({
>   _onClickSubmit() {
>     // do stuff
>   },
> 
>   // other stuff
> });
> 
> // good
> class extends React.Component {
>   onClickSubmit() {
>     // do stuff
>   }
> 
>   // other stuff
> }
> ```

> ```javascript
> // Demo: 13.4
> // bad
> render() {
>   (<div />);
> }
> 
> // good
> render() {
>   return (<div />);
> }
> ```

> ```javascript
> // Demo: 15
> import React, { PropTypes } from 'react';
> 
> const propTypes = {
>   id: PropTypes.number.isRequired,
>   url: PropTypes.string.isRequired,
>   text: PropTypes.string,
> };
> 
> const defaultProps = {
>   text: 'Hello World',
> };
> 
> class Link extends React.Component {
>   static methodsAreOk() {
>     return true;
>   }
> 
>   render() {
>     return <a href={this.props.url} data-id={this.props.id}>{this.props.text}</a>
>   }
> }
> 
> Link.propTypes = propTypes;
> Link.defaultProps = defaultProps;
> 
> export default Link;
> ```

1. Only include one React component per file
2. Always use JSX syntax
3. Use ```class extends React.Component``` over ```React.createClass```
4. If there are no state or refs, use normal functions (not arrow functions) over classes
5. Naming
  1. Use .jsx extension for React components
  2. Use PascalCase for filenames
  3. Reference Naming: Use PascalCase for React components and camelCase for their instances (because instances are variables)
  4. Component Naming: Use the filename as the component name (For example, ReservationCard.jsx should have a reference name of ReservationCard)
6. Instead, name the component by reference
7. Follow proper alignment styles for JSX syntax, See demo 7
8. Quotes
  1. Use double quotes (") for JSX attributes
  2. single quotes for all other JS
  * Regular HTML attributes also typically use double quotes instead of single, so JSX attributes mirror this convention
9. Spacing
  1. Include a single space in self-closing tag
  2. Do not pad JSX curly braces with spaces
10. Props
  1. Always use camelCase for prop names
  2. Omit the value of the prop when it is explicitly ```true```
  3. Always include an alt prop on <img> tags
    * If the image is presentational, alt can be an empty string 
    * Or, the <img> must have ```role="presentation"```
    * Do not use words like "image", "photo", or "picture" in ```<img>``` ```alt``` props (Why? Screenreaders already announce img elements as images, so there is no need to include this information in the alt text)
  4. Use only valid, non-abstract [ARIA roles](https://www.w3.org/TR/wai-aria/roles#role_definitions)
  5. Do not use ```accessKey``` on elements (Why? Inconsistencies between keyboard shortcuts and keyboard commands used by people using screenreaders and keyboards complicate accessibility)
  6. Avoid using an array index as ```key``` prop, prefer a unique ID. [Read why](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318)
11. Paranthesis
  1. Wrap JSX tags in parentheses when they span more than one line
12. Tags
  1. Always self-close tags that have no children
  2. If a component has multi-line properties, close its tag on a new line
13. Methods
  1. Use arrow functions to close over local variables
  2. Bind event handlers for the render method in the constructor
  3. Do not use underscore prefix for internal methods of a React component
  4. Always return a value in the ```render``` methods
14. Ordering for ```class extends React.Component```
  1. optional ```static``` methods
  2. ```constructor```
  3. ```getChildContext```
  4. ```componentWillMount```
  5. ```componentDidMount```
  6. ```componentWillReceiveProps```
  7. ```shouldComponentUpdate```
  8. ```componentWillUpdate```
  9. ```componentDidUpdate```
  10. ```componentWillUnmount```
  11. clickHandlers or eventHandlers like ```onClickSubmit()``` or ```onChangeDescription()```
  12. getter methods for render like ```getSelectReason()``` or ```getFooterContent()```
  13. Optional render methods like ```renderNavigation()``` or ```renderProfilePicture()```
  14. ```render```
15. How to define ```propTypes```, ```defaultProps```, ```contextTypes```, etc  - see Demo 15


> ```javascript
> // Demo: 

> ```

> ```javascript
> // Demo: 

> ```


















