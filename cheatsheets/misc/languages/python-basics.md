# Python Basics

## Hello World

```python
print("Hello, World!")
```

`python filename.py` to run the program.

## Comments, Variables and Global Variables
```python
# This is a comment.

"""
This is a comment
written in
more than just one line
"""

x = 5
y = "John"

x, y, z = "Orange", "Banana", "Cherry"
x = y = z = "Orange"
```

Global vars:
```python
# If you use the global keyword, the 
# variable belongs to the global scope

def myfunc():
  global x
  x = "fantastic"

myfunc()

print("Python is " + x)
```

## Data Types, Numbers, Casting

```python

# Python has the following data types 
# built-in by default,

x = "Hello World"                            # String 
x = 20                                       # Integer
x = 20.5                                     # Float
x = True                                     # Boolean
x = None                                     # NoneType

x = b"Hello"                                 # bytes
x = bytearray(5)                             # bytes array
x = memoryview(bytes(5)                      # memory view
x = 1j                                       # complex

x = ["apple", "banana", "cherry"]            # List
x = ("apple", "banana", "cherry")            # Tuple
x = range(6)                                 # Range
x = {"name" : "John", "age" : 36}            # Dict
x = {"apple", "banana", "cherry"}            # Set
x = frozenset({"apple", "banana", "cherry"}) # Frozen Set

# There may be times when you want to specify a type 
# on to a variable. This can be done with casting.

x = int(1)   # x will be 1
y = int(2.8) # y will be 2
z = int("3") # z will be 3
a = str(10)  # a will be "10"
```

## If ... Else, Booleans

```python
# Normal if...else block

a = 200
b = 33
if b > a:
  print("b is greater than a")
elif a == b:
  print("a and b are equal")
else:
  print("a is greater than b")
  
# Short-hand If
print("A") if a > b else print("B")


# Boolean vars
foo = True
bar = False

bool(bar)  # False
```

## While and For loops

```python
# While loop
i = 1
while i < 6:
  print(i)
  i += 1
  
# For (range loops)
for i in range(0, 10, 1):
  pass
  
# For (in loop)
for data in array:
  pass
```

## Strings

```python
# Strings

a = """Lorem ipsum dolor sit amet,
consectetur adipiscing elit,
sed do eiusmod tempor incididunt
ut labore et dolore magna aliqua."""

b = "Hello, World"

# String Slicing 
b[2:5]               # llo

# Modifying Strings (more on reference)
b.upper()            # HELLO, WORLD!
b.lower()            # hello, world!
b.replace("H", "J")  # Jello, World!
b.split(",")         # ['Hello', ' World!']

# Concatenate Strings
c = b + b            # Hello, WorldHello, World

# Format Strings
quantity = 3
itemno = 567
price = 49.95
myorder = "I want {} pieces of item {} for {} dollars."
print(myorder.format(quantity, itemno, price))

# Escape Characters (check reference for more)
txt = "We are the so-called \"Vikings\" from the north."

# Strings Methods
```

## Functions

```python
# Creating a function
def my_function(param1, param2):
  print(param1, param2)
  
my_function()  # calling it

# Default parameter value
def my_function(country = "Norway"):
  print("I am from " + country)

# Arbitrary Arguments, *args
# If you do not know how many arguments will be passed on
def my_function(*kids):
  print("The youngest child is " + kids[2])

my_function("Emil", "Tobias", "Linus")

# Keyword Arguments
def my_function(child3, child2, child1):
  print("The youngest child is " + child3)

my_function(child1 = "Emil", child2 = "Tobias", child3 = "Linus")

# Arbitrary Keyword Arguments, **kwargs
# If you do not know how many keyword arguments that will be passed into your function
def my_function(**kid):
  print("His last name is " + kid["lname"])

my_function(fname = "Tobias", lname = "Refsnes")

```

## Try ... Except

```python
# When an error occurs, or exception as we call it, 
# Python will normally stop and generate an error message.

# It can be simple
try:
  print(x)
except:
  print("An exception occurred")

# Or it can be complex
try:
  print(x)
except NameError:
  print("Variable x is not defined")
except:
  print("Something else went wrong")
else:
  print("Nothing went wrong")
finally:
  print("The 'try except' is finished")
```

## Lists, Tuple, Sets, Dictionaries

List
```python
mylist = ["apple", "banana", "cherry"]

len(mylist)   # 3
type(mylist)  # <class 'list'>

# Accessing list items
thislist = ["apple", "banana", "cherry", "orange", "kiwi", "melon", "mango"]

thislist[1]   # returns banana
thislist[-1]  # returns kiwi
thislist[2:5] # returns ['cherry', 'orange', 'kiwi']
thislist[:4]  # returns ['apple', 'banana', 'cherry', 'orange']

# Changing list items
thislist[1] = "blackcurrant"                    # changes banan to blackcurrant
thislist[1:3] = ["blackcurrant", "watermelon"]  # changes the items in the range
thislist.insert(2, "watermelon")   # inserts a new item without replacing any index shifts all left ones to one ++ index

# Add list items
thislist.append("orange")  #adds item to the end of the list

# Adding elements from one list to the other
thislist = ["apple", "banana", "cherry"]
tropical = ["mango", "pineapple", "papaya"]
thislist.extend(tropical)  

# Remove list items
thislist.remove("banana")  # removes the specified item
thislist.pop()             # removes the last item
thislist.pop(1)            # removes specified index
del thislist[0]            # removes specified index
thislist.clear()           # returns you []

# Sort lists
thislist.sort()                # sorts alphabetically or numerically
thislist.sort(reverse = True)  # sorts in decending order
thislist.reverse()             # reverses a list order 
```

Tuple
```python
# A tuple is a collection which is ordered and unchangeable.
mytuple = ("apple", "banana", "cherry")

len(thistuple)  # returns you the length of tuple "3"

# Access tuples
thistuple[1]   # returns you "banana"
thistuple[-1]  # returns you "cherry"
# same [2:5], [:3] ranges work with tuples

# Update tuples
# remember you cannot remove or update tuples they are unmutable
# but you can convert them to lists than back to tuples if you 
# really need to edit them
x = ("apple", "banana", "cherry")
y = list(x)
y[1] = "kiwi"
x = tuple(y)

# or you can update tuples by adding two tuples
thistuple = ("apple", "banana", "cherry")
y = ("orange",)
thistuple += y

# Unplack tuples
fruits = ("apple", "banana", "cherry")

(green, yellow, red) = fruits

print(green)   # apple
print(yellow)  # banana
print(red)     # cherry

```

Sets
```python
# A set is a collection which is unordered, unchangeable*, and 
# unindexed and duplicate values inside will be ignored
myset = {"apple", "banana", "cherry"}

# you can create this way too
thisset = set(("apple", "banana", "cherry"))

# You cannot access items in a set by referring to an index or a key.

# Add set items
thisset = {"apple", "banana", "cherry"}
thisset.add("orange")

thisset = {"apple", "banana", "cherry"}
tropical = {"pineapple", "mango", "papaya"}
thisset.update(tropical)

# Removing set items
thisset = {"apple", "banana", "cherry"}
thisset.remove("banana")
# or
thisset = {"apple", "banana", "cherry"}
thisset.discard("banana")
x = thisset.pop() # removes the last item

# Clearing the set
thisset.clear()
del thisset
```

Dictionary
```python
# Dictionaries are used to store data values in key:value pairs.
thisdict = {
  "brand": "Ford",
  "model": "Mustang",
  "year": 1964
}

# Access items
x = thisdict["model"]
x = thisdict.get("model")
x = thisdict.keys()    # returns you all of the keys of dict
x = thisdict.values()  # returns you all of the values

# Change items
thisdict["year"] = 2018
thisdict.update({"year": 2020})

# Add items
thisdict["color"] = "red"
thisdict.update({"color": "red"})

# Delete items
thisdict.pop("model")
thisdict.popitem()  # removes the last key,value pair
del thisdict["model"]

thisdict.clear() # empties the dict
```

### Folder Structure

- `/scripts` or `/bin` for that kind of command-line interface stuff
- `/tests` for your tests
- `/lib` for your C-language libraries
- `/doc` for most documentation
- `/apidoc` for the Epydoc-generated API docs
- `/src` -- source code
- `LICENSE`
- `setup.py`
- `requirements.txt`
- `.gitignore`