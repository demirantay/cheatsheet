# Javascript

Table of Contents
- [Installation](#installation)
- [Comments, Variables, Const, Operators](#comments-variables-let-const-operators)
- [Data Types, Functions, Objects, Events](#data-types-functions-objects-events)
- [Strings, String Methods, String Serach, String Templates](#strings-string-methods-string-serach-string-templates)
- [Numbers, Number Methods, Arrays, Array Methods, Array Sort](#numbers-number-methods-arrays-array-methods-array-sort)
- [Array Iteration, Array Const, Dates, Date Formats, Date Get&Set](#array-iteration-array-const-dates-date-formats-date-getset)
- [Math, Random, Booleans, Comparisons, If Else](#math-random-booleans-comparisons-if-else)
- [Loop For, Loop For In, Loop For Of, Loop While, Break](#loop-for-loop-for-in-loop-for-of-loop-while-break)
- [Iterables, Sets, Maps](#iterables-sets-maps)
- [Type Conversion, RegExp, Errors, Scope](#type-conversion-regexp-errors-scope)
- [Hoisting, Strict Mode, This keyword, Arrow function](#hoisting-strict-mode-this-keyword-arrow-function)
- [Classes, Modules, JSON](#classes-modules-json)
- [Debugging, Style Guide](#debugging-style-guide)

## Installation

```html
<!-- You can write pure js between two <script> tags -->
<script>
  document.getElementById("demo").innerHTML = "My First JavaScript";
</script>

<!-- Scripts can also be placed in external files: -->
<script src="myScript.js"></script>
```

## Comments, Variables, Let, Const, Operators

```js
// This is a single line comment

/*
The code below will change
the heading with id = "myH"
and the paragraph with id = "myP"
in my web page:
*/

// Variables
var x = 5;
var y = 6;

let x = 5;
let y = 6;

// Undeclared Vars
x = 5;
y = 6;

// Const
const PI = 3.141592653589793;
PI = 3.14; // This will give an error cannot be changed

// Let
// variables defined with let cannot be Redeclared.
let x = "John Doe";
let x = 0; // snytax error

// Operators (most are same but just look at this)
==	 // equal to 
===	 // equal value and equal type

```

## Data Types, Functions, Objects, Events

```js
// Data Types
let length = 16;                               // Number
let lastName = "Johnson";                      // String
let x = {firstName:"John", lastName:"Doe"};    // Object
let car;                                       // Undefined 

// Functions
function myFunction(p1, p2) {
  return p1 * p2; 
}

// Objects

// Events

```

## Strings, String Methods, String Serach, String Templates

## Numbers, Number Methods, Arrays, Array Methods, Array Sort

## Array Iteration, Array Const, Dates, Date Formats, Date Get&Set

## Math, Random, Booleans, Comparisons, If Else

## Loop For, Loop For In, Loop For Of, Loop While, Break

## Iterables, Sets, Maps

## Type Conversion, RegExp, Errors, Scope

## Hoisting, Strict Mode, This keyword, Arrow function

## Classes, Modules, JSON

## Debugging, Style Guide