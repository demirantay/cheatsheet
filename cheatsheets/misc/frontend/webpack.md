# Webpack

> Modren sites are built with Javascript not just plain-html

Table of Contents
- [Installation](#installation)
- [Basic Configuration](#basic-configuration)
- [Plugins](#plugins)
- [Modules and Loaders](#modules-and-loaders)
- [Development](#development)

## Installation

First setup node
```sh
mkdir project && cd project
npm init -y # creates a default package.json
```
core tech for webpack - donwload it
```sh
npm i -D webpack webpack-cli
```

Add this for this cheathseets sake:
```js
// src/index.js
console.log('Interesting!')
```

## Basic Configuration

Create a `webpack.config.js` in the root of your project.
- `Entry` -- The first part of setting up a webpack config is defining the entry point
  ```js
  const path = require('path')

  module.exports = {
    entry: {
      main: path.resolve(__dirname, './src/index.js'),
    },
  }
  ```
- `Output` -- The output is where the bundled file will resolve. For example we'll have it output in the dist folder.
  ```js
  module.exports = {
    /* ... */

    output: {
      path: path.resolve(__dirname, './dist'),
      filename: '[name].bundle.js',
    },
  }
  ```

## Plugins

webpack has a plugin interface that makes it flexible. Internal webpack code and third party extensions use plugins. Most apps use the generic ones.

- `HTML template file` - `!IMPORTANT AND DID NOT UNDERSTAND`

- `Clean` - clean-webpack-plugin, which clears out anything in the dist folder after each build. This is important to ensure no old data gets left behind.
  
  ```js
  const path = require('path')

  const HtmlWebpackPlugin = require('html-webpack-plugin')
  const { CleanWebpackPlugin } = require('clean-webpack-plugin')

  module.exports = {
    /* ... */

    plugins: [
      /* ... */
      new CleanWebpackPlugin(),
    ],
  }
  ```

## Modules and Loaders

webpack uses loaders to preprocess files loaded via modules. This can be JavaScript files, static assets like images and CSS styles, and compilers like TypeScript and Babel.

- `Babel (JavaScript)` - Babel is a tool that allows us to use tomorrow's JavaScript, today. There are a few additional dependencies for Babel as well. First download them:

  ```sh
  npm i -D babel-loader @babel/core @babel/preset-env @babel/preset-env @babel/plugin-proposal-class-properties
  ```
  
  ```js
  module.exports = {
    /* ... */

    module: {
      rules: [
        // JavaScript
        {
          test: /\.js$/,
          exclude: /node_modules/,
          use: ['babel-loader'],
        },
      ],
    },
  }
  ```
  Now Babel is set up, but our Babel plugin is not. To fix this, simply create a `.babelrc` file in the root of your project
  
  ```js
  # .babelrc
  
  {
    "presets": ["@babel/preset-env"],
    "plugins": ["@babel/plugin-proposal-class-properties"]
  }
  ```
  Then just run `npm run build` everything is set! you can now use all of new ES6 features of javascript to offer!
  

- `Images` - You'll want to be able to import images directly into your JavaScript files, but that's not something that JavaScript can do by default.

- `Fonts and inline` -

- `Styles` -

## Development