# Python Advanced

## Lambda

```python
# A lambda function is a small anonymous function.
# lambda arguments : expression

x = lambda a, b : a * b
print(x(5, 6))

# The power of lambda is better shown when you use 
# them as an anonymous function inside another function.
def myfunc(n):
  return lambda a : a * n
```

## Classes, Objects, Inheritance

Classes/Objects
```python
# Python is an object oriented programming language.
# Almost everything in Python is an object, with its 
# properties and methods.

class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age
    
  def myfunc(self):
    print("Hello my name is " + self.name)

# the self does not have to be named `self` it is just
# a first parameter that shows references to the class itself

p1 = Person("John", 36)
```

> The `__init__`, `__str__` (methods are called `magic methods/dunder methods` you can search them)

Inheritance
```python
# Inheritance allows us to define a class that inherits all 
# the methods and properties from another class.

# Parent Class
class Person:
  def __init__(self, fname, lname):
    self.firstname = fname
    self.lastname = lname

  def printname(self):
    print(self.firstname, self.lastname)

# Child Class
class Student(Person):
  pass
  
x = Student("Mike", "Olsen")
x.printname()

# --------

# If you add a __init__ func to a child class it 
# overrides the parents one, but you can manuevur
# this by calling the parents init function

class Student(Person):
  def __init__(self, fname, lname):
    Person.__init__(self, fname, lname)
    
# or you can use super() instead of the parents class
# name, it automatically selects the parent
```

## Iterators, Scope, Modules

Iterators
```python
# An iterator is an object that can be iterated upon, meaning that 
# you can traverse through all the values.

# Technically, in Python, an iterator is an object which implements 
# the iterator protocol, which consist of the methods __iter__() and __next__()

mytuple = ("apple", "banana", "cherry")
myit = iter(mytuple)

print(next(myit))  # apple
print(next(myit))  # banana
print(next(myit))  # cherry

# To create an object/class as an iterator you have to implement 
# the methods __iter__() and __next__() to your object.
```

Scope
```python
# If you need to create a global variable, but are stuck in the 
# local scope, you can use the global keyword
def myfunc():
  global x
  x = 300

myfunc()

print(x)
```

Modules
```python
# Consider a module to be the same as a code library.
# A file containing a set of functions you want to 
# include in your application

import mymodule
import mymodule as mx
from mymodule import func_name
```

## Dates, Math

Dates
```python
# A date in Python is not a data type of its own, but we can 
# import a module named datetime to work with dates as date objects.

import datetime

# creating data objsects from class
x = datetime.datetime(2020, 5, 17)
y = datetime.datetime.now()
```

Math
```python
# Python has a set of built-in math functions, 
# including an extensive math module

import math

# built in python
x = min(5, 10, 25)  # 5
y = max(5, 10, 25)  # 25

x = pow(4, 3)       # 4^3

# math module
x = math.sqrt(64)   # returns square root
x = math.pi         # 3.15...
x = math.ceil(1.4)  # 2
y = math.floor(1.4) # 1
```

## JSON, RegEx

JSON
```python
# Python has a built-in package called json, which 
# can be used to work with JSON data.

import json

""" Convert from JSON to Python"""

# some JSON:
x =  '{ "name":"John", "age":30, "city":"New York"}'

# parse x:
y = json.loads(x)

# the result is a Python dictionary:
print(y["age"])

""" Convert from Python to JSON """
# a Python object (dict):
x = {
  "name": "John",
  "age": 30,
  "city": "New York"
}

# convert into JSON:
y = json.dumps(x)
```

RegEx
```python
# A RegEx, or Regular Expression, is a sequence of characters 
# that forms a search pattern. RegEx can be used to check if 
# a string contains the specified search pattern.

import re

txt = "The rain in Spain"
x = re.search("^The.*Spain$", txt)  
# Search the string to see if it starts with "The" and ends with "Spain":
```
There are lots of things for regex [check basic reference from here](https://www.w3schools.com/python/python_regex.asp)

## User input, String formatting

User Input
```python
username = input("Enter username:")
print("Username is: " + username)
```

String Formatting
```python
# To make sure a string will display as expected, we 
# can format the result with the format() method.

myorder = "I want {} pieces of item number {} for {:.2f} dollars."
print(myorder.format(quantity, itemno, price))

# Indexed string formatting
myorder = "I want {0} pieces of item number {1} for {2:.2f} dollars."
print(myorder.format(quantity, itemno, price))

# or like this
txt = "His name is {1}. {1} is {0} years old."
print(txt.format(age, name))

# Named indexes
myorder = "I have a {carname}, it is a {model}."
print(myorder.format(carname = "Ford", model = "Mustang"))
```

## Decorators

> Return to this later on a little bit confusing

```python
# A decorator is a function that takes a function as its only 
# parameter and returns a function. This is helpful to “wrap” 
# functionality with the same code over and over again.
def decorate_message(fun):

    # Nested function
    def addWelcome(site_name):
        return "Welcome to " + fun(site_name)

    # Decorator returns a function
    return addWelcome

@decorate_message
def site(site_name):
    return site_name;

print site("StackOverflow")

# Out[0]: "Welcome to StackOverflow"
```