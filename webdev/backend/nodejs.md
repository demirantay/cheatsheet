# Node.js

### What is Node.js

JavaScript is a programming language designed for scripts in the browser. A JS script is a text file (just like html and css) that the browser receives and executes. This is done by a part of the browser called the JavaScript engine.

When in 2008 Google released Chrome, it gained popularity very rapidly. One of the many reasons for that popularity is it's very fast JavaScript engine.

Chrome's underlying code (including it's JS engine) is open source. So a developer named Ryan Dahl basically copied the JS engine code and put it into a standalone program which he called NodeJS. NodeJS is in essence the JS engine from chrome but without all the browser stuff: no document (webpage), no user interface, etc. It just runs the code in a JS file.

What is node used for? Anything really that you can program. Desktop applications (for example discord, VsCode are programmed with JS), mobile apps (Progressive web apps, react native, etc), but most importantly servers.

You can write your own server code that connects your frontend (browser JS) to for example a database. This can be a massive benefit for developers as it does not force you to use different languages for the frontend (which needs JS) and backend (PHP, C#, Python, Java, etc). You can now use JS for everything which makes it easier for a developer to work on the full stack (frontend, backend, database, etc).

## Hello, World!

```js
console.log("Hello, World!);
```
Run it with `node filename.js`

## Getting Started

```js
// Helo World
var http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.end('Hello World!');
}).listen(8080);

```
run `node filename.js`

## Modules, HTTP Module, File System

Modules
```js
// including modules
var http = require('http');

// exporting modules
exports.myDateTime = function () {
  return Date();
};

// use `exports` keyword and include your own file
var dt = require('./myfirstmodule');
```

HTTP Module
```js
var http = require('http');

// creating a web server
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'});
  res.write('Hello World!');
  res.end();
}).listen(8080);
```

File System
```js
/*
  Common use for the File System module:
  - Read files
  - Create files
  - Update files
  - Delete files
  - Rename files
*/

var fs = require('fs');

// Creating a file
fs.appendFile('mynewfile1.txt', 'Hello content!', function (err) {
  if (err) throw err;
  console.log('Saved!');
});

// Updating a file
fs.appendFile('mynewfile1.txt', ' This is my text.', function (err) {
  if (err) throw err;
  console.log('Updated!');
});

// Deleting a file
fs.unlink('mynewfile2.txt', function (err) {
  if (err) throw err;
  console.log('File deleted!');
});

// Reading a file
fs.readFile('demofile1.html', function(err, data) {
  if (err) throw err;
  console.log('File deleted!');
});
```

## URL Module, NPM, Events

URL Module
```js

```

NPM

using npm packages in node:
```sh
npm install upper-case
```
```js
var uc = require('upper-case');

// code
```

Events Module
```js
// Every action on a computer is an event. Like when a connection is made or a file is opened.
// Node.js has a built-in module, called "Events", where you can create-, fire-, and listen for- your own events.
var events = require('events');

//  all event properties and methods are an instance of an EventEmitter object. Create one to use events.
var eventEmitter = new events.EventEmitter();

//Create an event handler:
var myEventHandler = function () {
  console.log('I hear a scream!');
}

//Assign the event handler to an event:
eventEmitter.on('scream', myEventHandler);

//Fire the 'scream' event:
eventEmitter.emit('scream');
```

## Uploaded Files, Email

Uploaded Files:

There is a very good module for working with file uploads, called "Formidable".
```sh

```
```js

```

Email
```js

```

