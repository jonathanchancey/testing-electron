# React - Learning

## Design Details

> This is a definition

# Lesson 1 - Codeacademy

[Learn React: JSX Cheatsheet | Codecademy](https://www.codecademy.com/learn/react-101/modules/react-101-jsx-u/cheatsheet)

```jsx
const h1 = <h1>Hello world</h1>;
```

is known as jsx. It's html in a js file

> JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

JSX is not readable as javescript by web browsers and must be compiled

### JSX Elements

```jsx
<h1>Hello world</h1>
```

this is a JSX element

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go.

> That means that a JSX element can be saved in a variable, passed to a function, stored in an object or array…you name it.

## JSX Attributes

JSX elements can have attributes, just like HTML elements can.

A single JSX element can have many attributes, just like in HTML:

```jsx
const panda = <img src='images/panda.jpg' alt='panda' width='500px' height='500px' />;
```

## JSX Outer Elements

The first opening tag and the final closing tag of a JSX expression must belong to the same JSX element!

If you notice that a JSX expression has multiple outer elements, the solution is usually simple: wrap the JSX expression in a `<div></div>`.

## Rendering JSX

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

ReactDOM.render(<h1>Hello world</h1>, document.getElementById('app'));
```

`ReactDOM.render()`‘s first argument should be a JSX expression, and it will be rendered to the screen.

You just learned that `ReactDOM.render()` makes its first argument appear onscreen. But where on the screen should that first argument appear?

The container element with the id below would be selected by `document.getElementById('container')`.

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<link rel="stylesheet" href="/styles.css">
	<title>Learn ReactJS</title>
</head>

<body>
  <span id="container"></span>
	<script src="https://content.codecademy.com/courses/React/react-course-bundle.min.js"></script>
  <script src="/app.compiled.js"></script>
</body>

</html>
```

self made example:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
var myList = (
  <ul>
    <li>one</li>
    <li>two</li>
    <li>four</li>
  </ul>
);

ReactDOM.render(myList, document.getElementById('app'));
```

## The Virtual DOM

One special thing about `ReactDOM.render()` is that it *only updates DOM elements that have changed*.

```jsx
const hello = <h1>Hello world</h1>;
 
// This will add "Hello world" to the screen:
 
ReactDOM.render(hello, document.getElementById('app'));
 
// This won't do anything at all:
 
ReactDOM.render(hello, document.getElementById('app'));
```

## Self-Closing Tags

JSX requires them

```jsx
//Fine in JSX:
 
  <br />
 
//NOT FINE AT ALL in JSX:
 
  <br>
```

## Curly Braces in JSX

use curly braces to evaluate javascript in jsx

```jsx
ReactDOM.render(
  <h1>{2 + 3}</h1>,
  document.getElementById('app')
);
```

## Variables in JSX

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.

```jsx
// Declare a variable:
const name = 'Gerdo';
 
// Access your variable 
// from inside of a JSX expression:
const greeting = <p>Hello, {name}!</p>;
```

## Event Listeners in JSX

JSX elements can have *event listeners*, just like HTML elements can. Programming in React means constantly working with event listeners.

You create an event listener by giving a JSX element a special *attribute*. Here’s an example:

```jsx
<img onClick={myFunc} />
```

An event listener attribute’s *name* should be something like `onClick` or `onMouseOver`: the word `on`, plus the type of event that you’re listening for. You can see a list of valid event names [here](http://facebook.github.io/react/docs/events.html#supported-events).

```jsx
function myFunc() {
  alert('Make myFunc the pFunc... omg that was horrible i am so sorry');
}
 
<img onClick={myFunc} />
```

Note that in HTML, event listener *names* are written in all lowercase, such as `onclick` or `onmouseover`. In JSX, event listener names are written in camelCase, such as `onClick` or `onMouseOver`.

## JSX Conditionals: If Statements That Don't Work

Great work! You’ve learned how to use curly braces to inject JavaScript into a JSX expression!

Here’s a rule that you need to know: you can not inject an `if` statement into a JSX expression.

This code will break:

```jsx
(
  <h1>
    {
      if (purchase.complete) {
        'Thank you for placing an order!'
      }
    }
  </h1>
)
```

What if you want a JSX expression to render, but only under certain circumstances? You can’t inject an `if` statement. What can you do?

You have lots of options. In the next few lessons, we’ll explore some simple ways to write *conditionals* (expressions that are only executed under certain conditions) in JSX.

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

let message;

if (user.age >= drinkingAge) {
  message = (
    <h1>
      Hey, check out this alcoholic beverage!
    </h1>
  );
} else {
  message = (
    <h1>
      Hey, check out these earrings I got at Claire's!
    </h1>
  );
}

ReactDOM.render(
  message, 
  document.getElementById('app')
);
```

if.js works, because the words if and else are not injected in between JSX tags. The if statement is on the outside, and no JavaScript injection is necessary.

## JSX Conditionals: &&

We’re going to cover one final way of writing conditionals in React: the `&&` operator.

Like the ternary operator, `&&` is not React-specific, but it shows up in React surprisingly often.

`&&` works best in conditionals that will sometimes do an action, but other times do *nothing at all*.

Here’s an example:

## .map in JSX

```jsx
const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map(person =>
  // expression goes here:
  <li>{person}</li>
);

// ReactDOM.render goes here:
ReactDOM.render(<ul>{peopleLis}</ul>,document.getElementById('app'))
```

![React%20-%20Learning%20139d92ba5e654481bc4e90686bfbe342/Untitled.png](React%20-%20Learning%20139d92ba5e654481bc4e90686bfbe342/Untitled.png)

## Keys

A `key` is a JSX attribute. The attribute’s *name* is `key`. The attribute’s *value* should be something unique, similar to an `id` attribute.

`keys` don’t do anything that you can see! React uses them internally to keep track of lists. If you don’t use keys when you’re supposed to, React might accidentally scramble your list-items into the wrong order.

```jsx
const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map((person,i) =>
  // expression goes here:
  <li key={'person_' + i}>{person}</li>
);
```

## React.createElement

> You can write React code without using JSX at all!

The following JSX expression:

```jsx
const h1 = <h1>Hello world</h1>;
```

can be rewritten without JSX, like this:

```jsx
const h1 = React.createElement(
  "h1",
  null,
  "Hello, world"
);
```

---

## Hello World, Part II... THE COMPONENT

React applications are made out of components.

> A component is a small, reusable chunk of code that is responsible for one job. That job is often to render some HTML, which often involves rendering HTML.

This code will create and render a new React component:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
 
class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
};
 
ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
);
```

On line 4, by subclassing `React.Component`, you create a new component class. This is not a component! A component class is more like a factory that produces components. When you start making components, each one will come from a component class.

```jsx
// creates a variable named React:
import React from 'react';
// creates a variable named ReactDOM:
import ReactDOM from 'react-dom';
// evaluates this variable and get a particular, imported JavaScript object:
React // { imported object properties here... }
```

The methods imported from `'react-dom'` are meant for interacting with the DOM. You are already familiar with one of them: `ReactDOM.render()`.

The methods imported from `'react'` don’t deal with the DOM at all. They don’t engage directly with anything that isn’t part of React.

All class components will have some methods and properties in common, thus `extends`

After we define our class component, we can use it to render as many instances of that component as we want.

Component Class names should be in UpperCamelCase

All JavaScript classes need a body.

Here’s what your class body would look like on its own, without the rest of the class declaration syntax. 

```jsx
{
  render() {
    return <h1>Hello world</h1>;
  }
}
```

This is a set of instructions explaining how to build a React component. 

So, let’s make a React component! It only takes one more line:

```jsx
<MyComponentClass />

```

To make a React component, you write a *JSX element.* Instead of naming your JSX element something like `h1` or `div` like you’ve done before, give it the same name as a *component class*. Voilà, there’s your *component instance!*

JSX elements can be either HTML-like, or component instances. JSX uses capitalization to distinguish between the two! That is the React-specific reason why component class names must begin with capital letters. In a JSX element, that capitalized first letter says, “I will be a component instance and not an HTML tag.”