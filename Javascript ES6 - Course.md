# Javascript ES6 - Learning

# ES6

## Let

Unlike `var`, when using `let`, a variable with the same name can only be declared once. Note the `"use strict"`. This enables Strict Mode, which catches common coding mistakes and "unsafe" actions. For instance:

```jsx
"use strict";
x = 3.14;
```

This will display an error that `x is not defined`.

When you declare a variable with the `var` keyword, it is declared globally, or locally if declared inside a function.

The `let` keyword behaves similarly, but with some extra features. When you declare a variable with the `let` keyword inside a block, statement, or expression, its scope is limited to that block, statement, or expression.

[https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/compare-scopes-of-the-var-and-let-keywords](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/es6/compare-scopes-of-the-var-and-let-keywords)

`i` declared in the `if` statement is a separate variable than `i` declared in the first line of the function. 

```jsx
function checkScope() {
  let i = 'function scope';
  if (true) {
    let i = 'block scope';
    console.log('Block scope i is: ', i);
  }
  console.log('Function scope i is: ', i);
  return i;
}
```

## Const

The keyword `let` is not the only new way to declare variables. In ES6, you can also declare variables using the `const` keyword.

`const` has all the awesome features that `let` has, with the added bonus that variables declared using `const` are read-only. They are a constant value, which means that once a variable is assigned with `const`, it cannot be reassigned.

variables declared with `const` should be UPPERCASE

It is important to understand that objects (including arrays and functions) assigned to a variable using `const` are still mutable. Using the `const` declaration only prevents reassignment of the variable identifier.

```jsx
const s = [5, 6, 7];
s = [1, 2, 3];
s[2] = 45;
console.log(s);
```

## Prevent object mutation

As seen in the previous challenge, `const` declaration alone doesn't really protect your data from mutation. To ensure your data doesn't change, JavaScript provides a function `Object.freeze` to prevent data mutation.

Once the object is frozen, you can no longer add, update, or delete properties from it. Any attempt at changing the object will be rejected without an error.

```jsx
let obj = {
  name:"FreeCodeCamp",
  review:"Awesome"
};
Object.freeze(obj);
obj.review = "bad";
obj.newProp = "Test";
console.log(obj);
```

## **Use Arrow Functions to Write Concise Anonymous Functions**

In JavaScript, we often don't need to name our functions, especially when passing a function as an argument to another function. Instead, we create inline functions. We don't need to name these functions because we do not reuse them anywhere else.

To achieve this, we often use the following syntax:

```jsx
const myFunc = function() {
  const myVar = "value";
  return myVar;
}

```

ES6 provides us with the syntactic sugar to not have to write anonymous functions this way. Instead, you can use **arrow function syntax**:

```jsx
const myFunc = () => {
  const myVar = "value";
  return myVar;
}
```

When there is no function body, and only a return value, arrow function syntax allows you to omit the keyword `return` as well as the brackets surrounding the code. This helps simplify smaller functions into one-line statements:

```jsx
const myFunc = () => "value";
```

Just like a regular function, you can pass arguments into an arrow function.

```jsx
const doubler = (item) => item * 2;
doubler(4);

```

`doubler(4)` would return the value `8`.

If an arrow function has a single parameter, the parentheses enclosing the parameter may be omitted.

```jsx
const doubler = item => item * 2;

```

It is possible to pass more than one argument into an arrow function.

```jsx
const multiplier = (item, multi) => item * multi;
multiplier(4, 2);
```

`multiplier(4, 2)` would return the value `8`.

## **Set Default Parameters for Your Functions**

In order to help us create more flexible functions, ES6 introduces *default parameters* for functions.

Check out this code:

```jsx
const greeting = (name = "Anonymous") => "Hello " + name;

console.log(greeting("John"));
console.log(greeting());
```

## **Use the Rest Parameter with Function Parameters**

In order to help us create more flexible functions, ES6 introduces the *rest parameter* for function parameters. With the rest parameter, you can create functions that take a variable number of arguments. These arguments are stored in an array that can be accessed later from inside the function.

Check out this code:

```jsx
function howMany(...args) {
  return "You have passed " + args.length + " arguments.";
}
console.log(howMany(0, 1, 2));
console.log(howMany("string", null, [1, 2, 3], { }));

```

The console would display the strings `You have passed 3 arguments.` and `You have passed 4 arguments.`.

The rest parameter eliminates the need to check the `args` array and allows us to apply `map()`, `filter()` and `reduce()` on the parameters array.

## **Use the Spread Operator to Evaluate Arrays In-Place**

ES6 introduces the *spread operator*, which allows us to expand arrays and other expressions in places where multiple parameters or elements are expected.

```jsx
const arr1 = ['JAN', 'FEB', 'MAR', 'APR', 'MAY'];
let arr2;

arr2 = [...arr1];  // Change this line

console.log(arr2);
```

`...arr` returns an unpacked array. In other words, it *spreads* the array. However, the spread operator only works in-place, like in an argument to a function or in an array literal. The following code will not work:

```
const spreaded = ...arr;
```

## **Use Destructuring Assignment to Extract Values from Objects**

*Destructuring assignment* is special syntax introduced in ES6, for neatly assigning values taken directly from an object.

Consider the following ES5 code:

```
const user = { name: 'John Doe', age: 34 };

const name = user.name;
const age = user.age;

```

`name` would have a value of the string `John Doe`, and `age` would have the number `34`.

Here's an equivalent assignment statement using the ES6 destructuring syntax:

```
const { name, age } = user;

```

Again, `name` would have a value of the string `John Doe`, and `age` would have the number `34`.

## **Use Destructuring Assignment to Assign Variables from Objects**

Destructuring allows you to assign a new variable name when extracting values. You can do this by putting the new name after a colon when assigning the value.

Using the same object from the last example:

```jsx
const user = { name: 'John Doe', age: 34 };

```

Here's how you can give new variable names in the assignment:

```jsx
const { name: userName, age: userAge } = user;
```

## **Use Destructuring Assignment to Assign Variables from Nested Objects**

You can use the same principles from the previous two lessons to destructure values from nested objects.

Using an object similar to previous examples:

```jsx
const user = {
  johnDoe: {
    age: 34,
    email: 'johnDoe@freeCodeCamp.com'
  }
};

```

Here's how to extract the values of object properties and assign them to variables with the same name:

```jsx
const { johnDoe: { age, email }} = user;
```

And here's how you can assign an object properties' values to variables with different names:

```jsx
const { johnDoe: { age: userAge, email: userEmail }} = user;
```