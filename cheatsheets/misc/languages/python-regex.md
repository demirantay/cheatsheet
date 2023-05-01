# Python Regex

A RegEx, or Regular Expression, is a sequence of characters that forms a search pattern.

```python
# pythons built in package
import re

# Search the string to see if it starts with "The" and ends with "Spain":
txt = "The rain in Spain"
x = re.search("^The.*Spain$", txt)

# re module functions 
x.finall()  # Returns a list containing all matches
x.search()  # Returns a Match object if there is a match anywhere in the string
x.split()   # Returns a list where the string has been split at each match
x.sub()     # Replaces one or many matches with a string

# findall
txt = "The rain in Spain"
x = re.findall("ai", txt)
print(x)  # ['ai', 'ai']

# search
txt = "The rain in Spain"
x = re.search("Portugal", txt)
print(x)  # None

# split
txt = "The rain in Spain"
x = re.split("\s", txt)
print(x)  # ['The', 'rain', 'in', 'Spain']

# sub
txt = "The rain in Spain"
x = re.sub("\s", "9", txt)
print(x)  # The9rain9in9Spain
```

Metacharacters:
- a

Special Sequences
- a