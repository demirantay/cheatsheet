# PHP cheatsheet

### Basics
```php
<?php // In HTML file PHP code must be started-enclosed with <?php tags 

// If your php file only contains PHP code, it is best practice
// to omit the php closing tag to prevent accidental output.

// Two forward slashes start a one-line comment.

# So will a hash (aka pound symbol) but // is more common

/*
     Surrounding text in slash-asterisk and asterisk-slash
     makes it a multi-line comment.
*/

// Use "echo" or "print" to print output
print('Hello ');
echo "World\n";
```
<br>

### Types, Vars, Constants
```php
// Variables begin with the $ symbol.
// You don't have to (and cannot) declare variables.
// Once you assign a value, PHP will create the variable with the right type.

$boolean = true;  // or TRUE or True
$boolean = FALSE; // or false or False

$int1 = 12;   // => 12
$int2 = -12;  // => -12
$int3 = 012;  // => 10 (a leading 0 denotes an octal number)

$float = 1.234;
$float = 1.2e3;

// Delete variable
unset($int1);

// Arithmetic
$sum        = 1 + 1; // 2
$difference = 2 - 1; // 1

// Shorthand arithmetic
$number = 0;
$number += 1;      // Increment $number by 1
echo $number++;    // Prints 1 (increments after evaluation)
echo ++$number;    // Prints 3 (increments before evaluation)
$number /= $float; // Divide and assign the quotient to $number

// Strings should be enclosed in single quotes;
$sgl_quotes = '$String'; // => '$String'

// Avoid using double quotes except to embed other variables
$dbl_quotes = "This is a $sgl_quotes."; // => 'This is a $String.'

// Enclose a variable in curly braces if needed
$number = 23;
$apples = "I have {$number} apples to eat.";   // => I have 23 apples to eat.

// String concatenation is done with .
echo 'This string ' . 'is concatenated';  // Returns 'This string is concatenated'

// Strings can be passed in as parameters to echo
echo 'Multiple', 'Parameters', 'Valid';  // Returns 'MultipleParametersValid'

// A constant is defined by using define()
// and can never be changed during runtime!
define("FOO", "something");

// access to a constant is possible by calling the chosen name without a $
echo FOO; // Returns 'something'
```
<br>

### Arrays, Output, Logic
```php

```
<br>

### Control Flow, Loops
```php

```
<br>

### Functions, Includes
```php

```
<br>

### Traits, Namespaces, Late Static Binding, Magic Constants 
```php

```
<br>

### Eror Handling
```php

```
<br>
