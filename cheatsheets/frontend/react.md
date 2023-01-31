# React

Table of Contents
- [Installation](#installation)
- [JSX, Rendering Elements, ES6](#jsx-rendering-elements-es6)
- [Compontents, Class, Props](#compontents-class-props)
- [Events, Conditionals, Lists](#events-conditionals-lists)
- [Forms, Router, Memo](#forms-router-memo)
- [CSS Styling, Sass Styling](#css-styling-sass-styling)
- [Hooks](#hooks)
- [useState, useEffect, useContext](#usestate-useeffect-usecontext)
- [useRef, useReducer, useCallback](#useref-usereducer-usecallback)
- [useMemo, Custom Hooks](#usememo-custom-hooks)

## Installation

CDN  Installation
```html
<head>
    <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
</head>
```

Create-react-app installation
```sh
# create application
npx create-react-app <app-name>

# run application
cd <app-name>
npm start
```

Hello World
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';

function Hello(props) {
  return <h1>Hello World!</h1>;
}

const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<Hello />);
```

## JSX, Rendering Elements, ES6

ES6
```es6
// react uses es6 so become familiar with it's new features

// Classes
class Car {
  constructor(name) {
    this.brand = name;
  }

  present() {
    return 'I have a ' + this.brand;
  }
}

class Model extends Car {
  constructor(name, mod) {
    super(name);
    this.model = mod;
  }  
  show() {
      return this.present() + ', it is a ' + this.model
  }
}
const mycar = new Model("Ford", "Mustang");
mycar.show();

const mycar = new Car("Ford");

// Arrow Functions
hello = function() {
  return "Hello World!";
}

hello = () => {
  return "Hello World!";
}

hello = (val) => "Hello " + val;

// Variables
let x = 5.6;

// Array Methods
const myArray = ['apple', 'banana', 'orange'];

const myList = myArray.map((item) => <p>{item}</p>)

// Destructuring
const vehicles = ['mustang', 'f-150', 'expedition'];

// ---old way
const car = vehicles[0];
const truck = vehicles[1];
const suv = vehicles[2];
// ---new way
const [car, truck, suv] = vehicles;


// Spread Operator
const numbersOne = [1, 2, 3];
const numbersTwo = [4, 5, 6];
const numbersCombined = [...numbersOne, ...numbersTwo];  // [1, 2, 3, 4, 5, 6]

// Modules
const name = "Jesse"
const age = 40

export { name, age }

import { name, age } from "./person.js";
import message from "./message.js";

// Ternary Operator
if (authenticated) {
  renderApp();
} else {
  renderLogin();
}

// becomes this
authenticated ? renderApp() : renderLogin();
```

JSX
```jsx
// JSX allows us to write HTML in React.
const myElement = <h1>I Love JSX!</h1>;
const myElement2 = React.createElement('h1', {}, 'I do not use JSX!');
const myElement3 = <h1>React is {5 + 5} times better with JSX</h1>;
const myElement4 = <input type="text" />;

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
root.render(myElement2);
root.render(myElement3);
root.render(myElement4);
```

Rendering Elements
```jsx
// to render multiple components put them inside a div
ReactDOM.render(
      <div>
         <HeadNavigation/>
         <LeftNavigation/>
         <Footer/>
      </div>,
      document.getElementById('root')
);
```

## Compontents, Class, Props

Components
```jsx
// Components are independent and reusable bits of code. They serve the same purpose 
// as JavaScript functions, but work in isolation and return HTML.

// Class Component
class Car extends React.Component {
  render() {
    return <h2>Hi, I am a Car!</h2>;
  }
}

// Function Component
function Car() {
  return <h2>Hi, I am a Car!</h2>;
}

// Rendering the component
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Car />);

// Components in components
function Car() {
  return <h2>I am a Car!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my Garage?</h1>
      <Car />
    </>
  );
}

// React is all about reusablity so always have a seperate library 
// for your componetns
```

Class
```jsx
/*
Before React 16.8, Class components were the only way to track state and 
lifecycle on a React component. Function components were considered "state-less".

With the addition of Hooks, Function components are now almost equivalent to
Class components. The differences are so minor that you will probably 
never need to use a Class component in React.

So that is why I am skipping class components
*/
```

Props
```jsx
// Props are arguments passed into React components.
// Props are passed to components via HTML attributes.
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}

const myElement = <Car brand="Ford" />;

// output: I am a Ford!
```

## Events, Conditionals, Lists

Events
```jsx
// Just like HTML DOM events, React can perform actions based on user events.
// React has the same events as HTML: click, change, mouseover etc.

// React events are written in camelCase syntax and written inside curly braces::
<button onClick={shoot}>Take the Shot!</button>

// To pass an argument to an event handler, use an arrow function.
function Football() {
  const shoot = (a) => {
    alert(a);
  }

  return (
    <button onClick={() => shoot("Goal!")}>Take the shot!</button>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Football />);
```

Conditionals
```jsx
// lets say we have the components `MadeGoal`, `MissedGoal`
function Goal(props) {
  const isGoal = props.isGoal;
  if (isGoal) {
    return <MadeGoal/>;
  }
  return <MissedGoal/>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Goal isGoal={false} />);
```

Lists
```jsx
// In React, you will render lists with some type of loop.
// The JavaScript map() array method is generally the preferred method.
function Car(props) {
  return <li>I am a { props.brand }</li>;
}

function Garage() {
  const cars = ['Ford', 'BMW', 'Audi'];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car brand={car} />)}
      </ul>
    </>
  );
}

// or as a dict
function Garage() {
  const cars = [
    {id: 1, brand: 'Ford'},
    {id: 2, brand: 'BMW'},
    {id: 3, brand: 'Audi'}
  ];
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <ul>
        {cars.map((car) => <Car key={car.id} brand={car.brand} />)}
      </ul>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Garage />);
```

## Forms, Router, Memo

Forms
```jsx
// Just like in HTML, React uses forms to allow users to interact with the web page.
```

Router
```jsx

```

Memo
```jsx
// Using memo will cause React to skip rendering a component if its props have not changed.
// This can improve performance.

// Skipping this for now I have not faced any performance problems
```

## CSS Styling, Sass Styling

CSS Styling
```jsx
/* There are many ways to style React with CSS
    - Inline styling
    - CSS stylesheets
    - CSS Modules
*/

// Inline
// To style an element with the inline style attribute, the value must be a JavaScript object:
<h1 style={{color: "red"}}>Hello Style!</h1>
<h1 style={{backgroundColor: "lightblue"}}>Hello Style!</h1>

// you can also do
const Header = () => {
  const myStyle = {
    color: "white",
    backgroundColor: "DodgerBlue",
    padding: "10px",
    fontFamily: "Sans-Serif"
  };
  return (
    <>
      <h1 style={myStyle}>Hello Style!</h1>
      <p>Add a little style!</p>
    </>
  );
}

// CSS stylesheet
// just import it in your react application
import './App.css';
```

Sass Styling
```jsx
// Same as css improts just include it in the head
import './my-sass.scss';
```

## Hooks

Hooks allow function components to have access to state and other React features. Because of this, class components are generally no longer needed. Hooks allow us to "hook" into React features such as state and lifecycle methods.
```jsx
// Example
import React, { useState } from "react";
import ReactDOM from "react-dom/client";

function FavoriteColor() {
  const [color, setColor] = useState("red");

  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
      <button
        type="button"
        onClick={() => setColor("red")}
      >Red</button>
      <button
        type="button"
        onClick={() => setColor("pink")}
      >Pink</button>
      <button
        type="button"
        onClick={() => setColor("green")}
      >Green</button>
    </>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<FavoriteColor />);
```

3 rules for react hooks:
- 1 - Hooks can only be called inside React function components.
- 2 - Hooks can only be called at the top level of a component.
- 3 - Hooks cannot be conditional

## useState, useEffect, useContext

useState
```jsx
// The React useState Hook allows us to track state in a function component.
// State generally refers to data or propertie
import { useState } from "react";


function FavoriteColor() {
  // Initialize useState
  const [color, setColor] = useState("");
  
  // Read State
  return <h1>My favorite color is {color}!</h1>
  
  // Update State
  return (
    <>
      <h1>My favorite color is {color}!</h1>
      <button
        type="button"
        onClick={() => setColor("blue")}
      >Blue</button>
    </>
  )
}
```
Lets see a good useState with a component
```jsx
function Car() {
  const [car, setCar] = useState({
    brand: "Ford",
    model: "Mustang",
    year: "1964",
    color: "red"
  });

  const updateColor = () => {
    setCar(previousState => {
      return { ...previousState, color: "blue" }
    });
  }

  return (
    <>
      <h1>My {car.brand}</h1>
      <p>
        It is a {car.color} {car.model} from {car.year}.
      </p>
      <button
        type="button"
        onClick={updateColor}
      >Blue</button>
    </>
  )
}
```

useEffect
```jsx
// The useEffect Hook allows you to perform side effects in your components.
// Some examples of side effects are: fetching data, directly updating the DOM, and timers.
import { useState, useEffect } from "react";
import ReactDOM from "react-dom/client";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    setTimeout(() => {
      setCount((count) => count + 1);
    }, 1000);
  });

  return <h1>I've rendered {count} times!</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Timer />);
```

useContext
```jsx
// React Context is a way to manage state globally.
// To illustrate, we have many nested components. The component at the top and 
// bottom of the stack need access to the state.

// Did not understand
```

## useRef, useReducer, useCallback

useRef
```jsx
// Did not understand now
```

useReducer
```jsx
// The useReducer Hook is similar to the useState Hook.
// It allows for custom state logic.
```

useCallback
```jsx
// ...
```

## useMemo, Custom Hooks

useMemo
```jsx
// ...
```

Custom Hooks
```jsx

```