# Java

Hello World:
```java
public class Main {
  public static void main(String[] args) {
    System.out.println("Hello World");
  }
}
```
compile and run it with:
```java
javac filename.java
java filename
```

# Java Basics

```java
// Variables
int myNum = 5;
float myFloatNum = 5.99f;
char myLetter = 'D';
boolean myBool = true;
String myText = "Hello";


// Constants
final int myNum = 15;
myNum = 20;  // will generate an error: cannot assign a value to a final variable


// Integer Data Types
byte myNum = 100;           // 128 to 127
short myNum = 5000;         // -32768 to 32767
int myNum = 100000;         // -2147483648 to 2147483647
long myNum = 15000000000L;  // -9223372036854775808 to 9223372036854775807


// Floating Data Types
float myNum = 5.75f;    // 3.4e−038 to 3.4e+038
double myNum = 19.99d;  // 1.7e−308 to 1.7e+308


/*
  In Java, there are two types of casting:
  
  Widening Casting (automatically) - converting a smaller type to a larger type size
  byte -> short -> char -> int -> long -> float -> double
  
  Narrowing Casting (manually) - converting a larger type to a smaller size type
  double -> float -> long -> int -> char -> short -> byte
*/

// Widening Casting
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double


// Narrowing Casting
double myDouble = 9.78d;
int myInt = (int) myDouble; // Manual casting: double to int


// Strings
String greeting = "Hello";
greeting.length()       // 5
greeting.toUpperCase()  // HELLO
greeting.toLowerCase()  // hello
greeting.indexOf("H")   // 0


// The Java Math class
Math.max(5, 10);  // returns highest parameter
Math.min(5, 10);  // returns lowest parameter
Math.sqrt(64);    // returns you the square root
Math.abs(-4.7);   // retrurns you the absolute positive value
Math.random();    // returns you a random number


// If ... Else
if (condition1) {
  //...
} else if (condition2) {
  // ...
} else {
  // ...
}


// Short Hand If...Else (Ternary Operator)
int time = 20;
String result = (time < 18) ? "Good day." : "Good evening.";


// While loop
int i = 0;
while (i < 5) {
  System.out.println(i);
  i++;
}


// Do While loop
do {
  System.out.println(i);
  i++;
}
while (i < 5);


// For loop
for (int i = 0; i < 5; i++) {
  System.out.println(i);
}


// For Each loop
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
for (String i : cars) {
  System.out.println(i);
}


// Arrays
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
int[] myNum = {10, 20, 30, 40};


// Multidimensional Arrays
int[][] myNumbers = { {1, 2, 3, 4}, {5, 6, 7} };


```java
public class Main {
  static void myMethod() {
    // ...
  }
}


// Functions with parameters
static void myMethod(String fname, int age) {
  System.out.println(fname + " is " + age);
}


// Functions with returning values (replace void)
static int myMethod(int x) {
  return 5 + x;
}


// Method Overloading
// With method overloading, multiple methods can have the same name with different parameters:
int myMethod(int x)
float myMethod(float x)
double myMethod(double x, double y)


// Exception .. Catching
try {
   // Protected code
} catch (ExceptionType1 e1) {
   // Catch block
} catch (ExceptionType2 e2) {
   // Catch block
} catch (ExceptionType3 e3) {
   // Catch block
} finally {
   // The finally block always executes.
}
```
There are MUCH more methods of each of these classes above however I just put the most used ones.

# Java OOP

Rules:
- There can be only one public class per source file.
- A source file can have multiple non-public classes.
- If the class is defined inside a package, then the package statement should be the first statement in the source file.

```java
// Class
public class Dog {
   String breed;
   int age;
   String color;

   void barking() {
   }

   void hungry() {
   }

   void sleeping() {
   }
}


// Class with a Constructor
public class Puppy {
   public Puppy() {
   }
}


// Class with multiple Constructors
public class Puppy {
   public Puppy() {
   }

   public Puppy(String name) {
      // This constructor has one parameter, name.
   }
}


// Object creation
Puppy myPuppy = new Puppy( "tommy" );


/*
In Java, just like methods, variables of a class too can have another class as its member. 
Writing a class within another is allowed in Java. The class written within is called the 
nested class, and the class that holds the inner class is called the outer class.
*/

class Outer_Demo {
   class Inner_Demo {
   }
}


// Inheritance
class Vehicle {
  protected String brand = "Ford";        // Vehicle attribute
  public void honk() {                    // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mustang";    // Car attribute
  
  public static void main(String[] args) {
    Car myCar = new Car();
    myCar.honk();
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
  
}


// Overriding

// In the previous chapter, we talked about superclasses and subclasses. 
// If a class inherits a method from its superclass, then there is a 
// chance to override the method provided that it is not marked final.

class Animal {
   public void move() {
      System.out.println("Animals can move");
   }
}

class Dog extends Animal {
   public void move() {
      System.out.println("Dogs can walk and run");
   }
}

public class TestDog {

   public static void main(String args[]) {
      Animal a = new Animal();   // Animal reference and object
      Animal b = new Dog();   // Animal reference but Dog object

      a.move();   // runs the method in Animal class
      b.move();   // runs the method in Dog class
   }
}


// Polymorphism

// Polymorphism is the ability of an object to take on many forms. 
// The most common use of polymorphism in OOP occurs when a parent 
// class reference is used to refer to a child class object.
public interface Vegetarian{}
public class Animal{}
public class Deer extends Animal implements Vegetarian{}

/*
Now, the Deer class is considered to be polymorphic
since this has multiple inheritance. Following are true for the above examples −

A Deer IS-A Animal
A Deer IS-A Vegetarian
A Deer IS-A Deer
A Deer IS-A Object

*/


// --------------------


// Abstraction
/*
abstraction is a process of hiding the implementation details from the user,
only the functionality will be provided to the user. In other words, the user 
will have the information on what the object does instead of how it does it.
*/



// --------------------

// Encapsulation
/*

Encapsulation in Java is a mechanism of wrapping the data (variables) and code 
acting on the data (methods) together as a single unit. In encapsulation, the 
variables of a class will be hidden from other classes, and can be accessed only 
through the methods of their current class. Therefore, it is also known as data hiding

*/

public class EncapTest {
   private String name;
   private String idNum;
   private int age;

   public int getAge() {
      return age;
   }

   public String getName() {
      return name;
   }

   public String getIdNum() {
      return idNum;
   }

   public void setAge( int newAge) {
      age = newAge;
   }

   public void setName(String newName) {
      name = newName;
   }

   public void setIdNum( String newId) {
      idNum = newId;
   }
}


// --------------------------------

// Interfaces

/*

An interface is a reference type in Java. It is similar to class. It is a collection of abstract methods. 
A class implements an interface, thereby inheriting the abstract methods of the interface.

Writing an interface is similar to writing a class. But a class describes the attributes and behaviors of an object. And an interface contains behaviors that a class implements.

Unless the class that implements the interface is abstract, all the methods of the interface need to be defined in the class.

*/

/* File name : Animal.java */
interface Animal {
   public void eat();
   public void travel();
}

/* File name : MammalInt.java */
public class MammalInt implements Animal {

   public void eat() {
      System.out.println("Mammal eats");
   }

   public void travel() {
      System.out.println("Mammal travels");
   } 

   public int noOfLegs() {
      return 0;
   }

   public static void main(String args[]) {
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
} 

```

### Modifiers

Modifiers are keywords that you add to those definitions to change their meanings. To use a modifier, you include its keyword in the definition of a class, method, or variable.

Java provides a number of access modifiers to set access levels for classes, variables, methods and constructors. The four access levels are 
- Visible to the package, the default. No modifiers are needed.
- Visible to the class only (private).
- Visible to the world (public).
- Visible to the package and all subclasses (protected).

Java provides a number of non-access modifiers to achieve many other functionality.
- The static modifier for creating class methods and variables.
- The final modifier for finalizing the implementations of classes, methods, and variables.
- The abstract modifier for creating abstract classes and methods.
- The synchronized and volatile modifiers, which are used for threads.

# Java Packages and API

A package in Java is used to group related classes. Packages are divided into two categories:
- Built-in Packages (packages from the Java API)
- User-defined Packages (create your own packages)

### Builtin Packages

```java
// The Java API is a library of prewritten classes, that are free to use
// The library is divided into packages and classes. Meaning you can either 
// import a single class (along with its methods and attributes), or a whole 
// package that contain all the classes that belong to the specified package.

import package.name.Class;   // Import a single class
import package.name.*;   // Import the whole package
```

### User Defined Packages

While creating a package, you should choose a name for the package and include a package statement along with that name at the top of every source file that contains the classes, interfaces, enumerations, and annotation types that you want to include in the package. The package statement should be the first line in the source file. There can be only one package statement in each source file

To compile the Java programs with package statements, you have to use -d option as shown below.
```
$ javac -d Destination_folder file_name.java
```

ex:
```java
/* File name : Animal.java */
package animals;

interface Animal {
   public void eat();
   public void travel();
}
```
and
```java
package animals;
/* File name : MammalInt.java */

public class MammalInt implements Animal {

   public void eat() {
      System.out.println("Mammal eats");
   }

   public void travel() {
      System.out.println("Mammal travels");
   } 

   public int noOfLegs() {
      return 0;
   }

   public static void main(String args[]) {
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
} 
```
then compile:
```
$ javac -d . Animal.java 
$ javac -d . MammalInt.java
```

### Import Keyoword

```java

/*
  If a class wants to use another class in the same package, the package 
  name need not be used. Classes in the same package find each other 
  without any special syntax.
*/


// However if you want to access a class in a package from a file that is 
// NOT inside that package you have to use import keywor

import packageName.*;
import packageName.className;

```
