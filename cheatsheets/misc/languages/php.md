# PHP framework



Hello World:
```php
<body>
      <?php echo "Hello, World!";?>
</body>
```

In order to run php you need:
- `Web Server` 
- `Database` 
- `php parsing engine`

You can run your php code with php parsing engine:
```html
<?php...?>
<?...?>
<%...%>
<script language = "PHP">...</script>
```
or you can run it on the terminal:
```
$ php test.php
```

# PHP Basics

```php
# single line comment
// single line comment
/* 
multiple line comment
*/


// Use "echo" or "print" to print output
// () tags are optional
print('Hello ');
echo "Wordl";


// Types and Variables
$foo = true;  # or TRUE, True
$foo = false; # or FALSE, False


// Integers
$int1 = 12;
$int2 = -12;
$int3 = 012;
$int4 = 0x0F;
$int5 = 0b11111111;


// Floats
$float = 1.234;
$float = 1.2e3;
$float = 7E-10;


// Null type
$my_var = NULL;
$my_var = null;


// Delete variable
unset($int1);


// Arithmetic
$sum        = 1 + 1; // 2
$difference = 2 - 1; // 1
$product    = 2 * 2; // 4
$quotient   = 2 / 1; // 2


// Shorthand arithmetic
$number = 0;
$number += 1; 
$number++;


// 'Spaceship' operator (since PHP 7)
// Returns 0 if values on either side are equal
// Returns 1 if value on the left is greater
// Returns -1 if the value on the right is greater
$a = 100;
$b = 1000;
echo $a <=> $a; // 0 since they are equal
echo $a <=> $b; // -1 since $a < $b
echo $b <=> $a; // 1 since $b > $a


// Strings should be enclosed in single quotes;
$foo = 'HELLO';


// Avoid using double quotes except to embed other variables
$bar = "This is a $foo."; // => 'This is a HELLO.'


// Special characters are only escaped in double quotes
$escaped   = "This contains a \t tab character.";
$unescaped = 'This just contains a slash and a t: \t';


// Enclose a variable in curly braces if needed
$apples = "I have {$number} apples to eat.";
$oranges = "I have ${number} oranges to eat.";
$money = "I have $${number} in the bank.";


// String concatenation is done with .
echo 'This string ' . 'is concatenated';


// A constant is defined by using define()
// and can never be changed during runtime!
define("FOO", "something");


// Control Structures
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


// While loop
$i = 0;
while ($i < 5) {
    echo $i++;
}


// Do ... While
$i = 0;
do {
    echo $i++;
} while ($i < 5);


// For loop
for ($x = 0; $x < 10; $x++) {
    echo $x;
}


// Foreach loops can iterate over arrays
$wheels = ['bicycle' => 2, 'car' => 4];

foreach ($wheels as $wheel_count) {
    echo $wheel_count;
}


// ARRAYS
$numbers = array( 1, 2, 3, 4, 5);  // numeric arrays
$salaries = array("mohammad" => 2000, "qadir" => 1000, "zara" => 500);  // associate arrays


// Functions
function my_function () {
    return 'Hello';
}

echo my_function(); // => "Hello"


// functions with pre-defined parameters
function add ($x, $y = 1) { // $y is optional and defaults to 1
    $result = $x + $y;
    return $result;
}

echo add(4); // => 5
echo add(4, 2); // => 6


// Since PHP 5.3 you can declare anonymous functions;
$inc = function ($x) {
    return $x + 1;
};

echo $inc(2); // => 3
```

# PHP Advanced

### Includes
```php
<?php
// PHP within included files must also begin with a PHP open tag.
include 'my-file.php';

include_once 'my-file.php';
// If the code in my-file.php has been included elsewhere, it will

require 'my-file.php';
require_once 'my-file.php';
// Same as include(), except require() will cause a fatal error if the
// file cannot be included.
```
OOP:
```php
class MyClass {
    const MY_CONST      = 'value'; // A constant
    static $staticVar   = 'static';
    
    // Static variables and their visibility
    public static $publicStaticVar = 'publicStatic';
    // Accessible within the class only
    private static $privateStaticVar = 'privateStatic';
    // Accessible from the class and subclasses
    protected static $protectedStaticVar = 'protectedStatic';
    
    // Properties must declare their visibility
    public $property    = 'public';
    public $instanceProp;
    protected $prot = 'protected'; // Accessible from the class and subclasses
    private $priv   = 'private';   // Accessible within the class only


    // Create a constructor with __construct
    public function __construct($instanceProp) 
        // Access instance variables with $this
        $this->instanceProp = $instanceProp;
    }
    
    // Methods are declared as functions inside a class
    public function myMethod() 
        print 'MyClass';
    }

    // final keyword would make a function unoverridable
    final function youCannotOverrideMe(){}
    
    
    // Magic Methods

    // what to do if Object is treated as a String
    public function __toString() {
        return $property;
    }

    // opposite to __construct()
    // called when object is no longer referenced
    public function __destruct() 
        print "Destroying";
    }
}


// Class constants can always be accessed statically
echo MyClass::MY_CONST;    

echo MyClass::$staticVar;  // Outputs 'static';
MyClass::myStaticMethod(); // Outputs 'I am static';

// Instantiate classes using new
$my_class = new MyClass('An instance property');

// Access class members using ->
echo $my_class->property;     // => "public"
echo $my_class->instanceProp; // => "An instance property"
$my_class->myMethod();        // => "MyClass"


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
```

### Magic Constants

```php
// Get current class name. Must be used inside a class declaration.
echo "Current class name is " . __CLASS__;

// Get full path directory of a file
echo "Current directory is " . __DIR__;
     // Typical usage
      require __DIR__ . '/vendor/autoload.php';
      
// Get full path of a file
echo "Current file path is " . __FILE__;

// Get current function name
echo "Current function name is " . __FUNCTION__;

// Get current line number
echo "Current line number is " . __LINE__;

// Get the name of the current method. Only returns a value when used inside a trait or object declaration.
echo "Current method is " . __METHOD__;

// Get the name of the current namespace
echo "Current namespace is " . __NAMESPACE__;

// Get the name of the current trait. Only returns a value when used inside a trait or object declaration.
echo "Current trait is " . __TRAIT__;
```

### Error Handliong

```php

// Simple error handling can be done with try catch block

try {
    // Do something
} catch (Exception $e) {
    // Handle exception
}

```