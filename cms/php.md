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
// Arrays
$array = ['One', 'Two', 'Three'];

echo $array[0]; // => "One"

// Add an element to the end of an array
$array[] = 'Four';

// or
array_push($array, 'Five');

// Remove element from array
unset($array[3]);

// or you can use arrays the old and associative way
$associative = ['One' => 1, 'Two' => 2, 'Three' => 3];
echo $associative['One']; // prints 1

/********************************
 * Output
 */

echo('Hello World!');
// Prints Hello World! to stdout.

print('Hello World!'); // The same as echo

/********************************
 * Logic
 */
$a = 0;
$b = '0';
$c = '1';
$d = '1';

// The following will only be true if the values match and are the same type.
assert($c === $d);
assert($a !== $d);
assert(1 === '1');
assert(1 !== '1');

// Variables can be converted between types, depending on their usage.

$string = '1';
echo $string + $string; // => 2 (strings are coerced to integers)

//or
$zero = 0;
$boolean = (boolean) $zero; // => false

$var = null; // Null value
```
<br>

### Control Flow, Loops
```php
/********************************
 * Control Structures
 */

$x = 0;
if ($x === '0') {
    print 'Does not print';
} elseif ($x == '1') {
    print 'Does not print';
} else {
    print 'Does print';
}

// ternary operator
print (false ? 'Does not get printed' : 'Does');

/********************************
 * Loops
 */

// while
$i = 0;
while ($i < 5) {
    echo $i++;
} // Prints "01234"

// do ... while
$i = 0;
do {
    echo $i++;
} while ($i < 5); // Prints "01234"

// for
for ($x = 0; $x < 10; $x++) {
    echo $x;
} // Prints "0123456789"


// Foreach loops can iterate over arrays
$wheels = ['bicycle' => 2, 'car' => 4];

foreach ($wheels as $wheel_count) {
    echo $wheel_count;
} // Prints "24"

// You can iterate over the keys as well as the values
foreach ($wheels as $vehicle => $wheel_count) {
    echo "A $vehicle has $wheel_count wheels";
}
```
<br>

### Functions, Includes
```php
/********************************
 * Functions
 */

function add ($x, $y = 1) { // $y is optional and defaults to 1
    $result = $x + $y;
    return $result;
}

echo add(4); // => 5
echo add(4, 2); // => 6

/********************************
 * Includes
 */

<?php
// PHP within included files must also begin with a PHP open tag.

include 'my-file.php';
// The code in my-file.php is now available in the current scope.
// If the file cannot be included (e.g. file not found), a warning is emitted.

include_once 'my-file.php';
// If the code in my-file.php has been included elsewhere, it will
// not be included again. This prevents multiple class declaration errors

require 'my-file.php';
require_once 'my-file.php';
// Same as include(), except require() will cause a fatal error if the
// file cannot be included.
```
<br>

### Classes

```php
/********************************
 * Classes
 */

// Classes are defined with the class keyword

class MyClass
{
    const MY_CONST      = 'value'; // A constant
    static $staticVar   = 'static';

    // Properties must declare their visibility
    public $property    = 'public';
    public $instanceProp;
    protected $prot = 'protected'; // Accessible from the class and subclasses
    private $priv   = 'private';   // Accessible within the class only

    // Create a constructor with __construct
    public function __construct($instanceProp) {
        // Access instance variables with $this
        $this->instanceProp = $instanceProp;
    }

    // Methods are declared as functions inside a class
    public function myMethod() {
        print 'MyClass';
    }

    // Magic Methods
    // what to do if Object is treated as a String
    public function __toString() {
        return $property;
    }
}

// --------

// Class constants can always be accessed statically
echo MyClass::MY_CONST;    // Outputs 'value';

// Instantiate classes using new
$my_class = new MyClass('An instance property');
// The parentheses are optional if not passing in an argument.

// Access class members using ->
echo $my_class->property;     // => "public"
echo $my_class->instanceProp; // => "An instance property"
$my_class->myMethod();        // => "MyClass"

// -----

// Extend classes using "extends"
class MyOtherClass extends MyClass
{
    function printProtectedProperty()
    {
        echo $this->prot;
    }

    // Override a method
    function myMethod()
    {
        parent::myMethod();
        print ' > MyOtherClass';
    }
}

$my_other_class = new MyOtherClass('Instance prop');
$my_other_class->printProtectedProperty(); // => Prints "protected"
$my_other_class->myMethod();               // Prints "MyClass > MyOtherClass"

// much more go back to learn x in y minutes ...
```

<br>

### Traits, Namespaces, Late Static Binding, Magic Constants 
```php
/********************************
 * Traits
 */
```
<br>

### Eror Handling
```php

```
<br>
