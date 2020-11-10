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
  
- __`Note`__ -- Before deploying your website to production, be mindful that unminified JavaScript can significantly slow down the page for your users. Make sure HTML loads, be sure to have `production.min.js`

<br>

## Create a New React App

<br>

## CDN Links

<br>

## Release Channels

<Br>

---

## Hello World

<br>

## Introducing JSX

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
