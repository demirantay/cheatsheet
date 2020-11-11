# React Docs Notes

- These notes are taken from the [main documentation guide](https://reactjs.org/docs/getting-started.html)

<br>

## Getting Started

- You can add React to an HTML page in one minute. You can then either gradually expand its presence, or keep it contained to a few dynamic widgets. When starting a React project, a simple HTML page with script tags might still be the best option. It only takes a minute to set up!

<Br>

## Add React to a Website

- As we said above you can add react as much or as little as you can to your app so if you would like to start out small just add a simple html script tag and build it from there. There will be no complicated tools or install requirements.

  First, open the HTML page you want to edit. Add an empty <div> tag to mark the spot where you want to display something with React. For example:
  ```html
  <!-- ... existing HTML ... -->

  <div id="like_button_container"></div>

  <!-- ... existing HTML ... -->
  ```
  Next, add three <script> tags to the HTML page right before the closing </body> tag:
  ```html
     <!-- ... other HTML ... -->

    <!-- Load React. -->
    <!-- Note: when deploying, replace "development.js" with "production.min.js". -->
    <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>

    <!-- Load our React component. -->
    <script src="like_button.js"></script>

  </body>
  ```
  The first two tags load React. The third one will load your component code. (Step 3: Create a React Component - Create a file called like_button.js next to your HTML page.) However since we have not learned how to create components in react wea re gonna skip this part. But you get the idea of how to include react into your html pages.
  
  By the way if you want to use JSX instead of native javascript you need to include the follownig at the bottom fo the page as well:
    ```html
    <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    ```
    
    (Adding JSX to a project doesn’t require complicated tools like a bundler or a development server. Essentially, adding JSX is a lot like adding a CSS preprocessor. The only requirement is to have Node.js installed on your computer.)
  
- __`Note`__ -- Before deploying your website to production, be mindful that unminified JavaScript can significantly slow down the page for your users. Make sure HTML loads, be sure to have `production.min.js`

<br>

## Create a New React App

- This page describes a few popular React toolchains which is used for scaling, debugging, optimizing .. etc. The toolchains recommended on this page don’t require configuration to get started. If you don’t experience the problems described above or don’t feel comfortable using JavaScript tools yet, consider adding React as a plain <script> tag on an HTML page, optionally with JSX.

### Create React App

- Create React App is a comfortable environment for learning React, and is the best way to start building a new single-page application in React. To create a project, run: 
  ```
  npx create-react-app my-app
  cd my-app
  npm start
  ```
  Create React App doesn’t handle backend logic or databases; it just creates a frontend build pipeline, so you can use it with any backend you want. Under the hood, it uses Babel and webpack, but you don’t need to know anything about them.

### Your own Toolchain

- If you prefer to set up your own JavaScript toolchain from scratch A JavaScript build toolchain typically consists of:
  - A package manager, such as Yarn or npm (for installation)
  - A bundler, such as webpack or Parcel. It lets you write modular code and bundle it together into small packages to optimize load time.
  - A compiler such as Babel. It lets you write modern JavaScript code that still works in older browsers.
  
<br>
---

## Introducing JSX

- Consider this variable declaration:
  ```js
  const element = <h1>Hello, world!</h1>;
  ```
  This funny tag syntax is neither a string nor HTML. It is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like

- __`Why JSX?`__ -- React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.

  React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.
  
- __`Embedding Expressions in JSX`__ -- In the example below, we declare a variable called name and then use it inside JSX by wrapping it in curly braces:
  ```js
  const name = 'Josh Perez';
  const element = <h1>Hello, {name}</h1>;

  ReactDOM.render(
    element,
    document.getElementById('root')
  );
  ```
  You can put any valid JavaScript expression inside the curly braces in JSX.
  
- __`JSX is an Expression Too`__ -- After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:
  ```js
  function getGreeting(user) {
    if (user) {
      return <h1>Hello, {formatName(user)}!</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
  }
  ```
  
- __`Specifying Attributes with JSX`__ -- You may use quotes to specify string literals as attributes:
  ```js
  const element = <div tabIndex="0"></div>;
  ```
  You may also use curly braces to embed a JavaScript expression in an attribute:
  ```js
  const element = <img src={user.avatarUrl}></img>;
  ```
  Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute.
  
- __`JSX Prevents Injection Attacks`__ -- It is safe to embed user input in JSX:
  ```js
  const title = response.potentiallyMaliciousInput;
  // This is safe:
  const element = <h1>{title}</h1>;
  ```
  By default, React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that’s not explicitly written in your application.
  
- __`JSX Represents Objects`__ -- Babel compiles JSX down to React.createElement() calls. For exmaple this code in jsx:
  ```js
  const element = (
    <h1 className="greeting">
      Hello, world!
    </h1>
  );
  ```
  is equal to this in javsacript:
  ```js
  const element = React.createElement(
    'h1',
    {className: 'greeting'},
    'Hello, world!'
  );
  ```

<Br>

## Rendering Elements 

<Br>

## Components and Props

<Br>

## State and Lifecycle

<br>

## Handling Events

<Br>

## Conditional Rendering 

<br>

## Lists and Keys

<br>

## Forms

<br>

## Lifting State Up

<br>

## Composition vs Inheritance

<br>

## Thinking in React
