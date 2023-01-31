# Python cheatsheet

## Basics


## Advanced

```python
# With *args you can pass on parameters 
# with already defined values
def myFun(*argv):
    for arg in argv:
        print (arg)
        
myFun('Hello', 'Welcome', 'to', 'GeeksforGeeks')


# with **kwargs you can add keyworded, variable-length 
# argument list as a paramter to a function
# One can think of the kwargs as being a dictionary that maps 
# each keyword to the value that we pass alongside it
def myFun(**kwargs):
    for key, value in kwargs.items():
        print ("%s == %s" %(key, value))

myFun(first ='Geeks', mid ='for', last='Geeks')  


# You can also combine args and kwargs together inside a paramter
def myFun(*args,**kwargs):
    print("args: ", args)
    print("kwargs: ", kwargs)
 
myFun('geeks','for','geeks',first="Geeks",mid="for",last="Geeks")
```


## Python Folder Structure

-` README` -- basic readme
- `config.py` -- if you have configs
- `requirements.txt` -- for pip dependencies
- `venv/` -- for virtualenv
- `/scripts` -- for that kind of command-line interface stuff
- `/tests` -- for your tests
- `/lib` -- for your C-language libraries
- `/doc` --  for most documentation
- `/apidoc` -- for the Epydoc-generated API docs.
- `/appname` or `/src` -- that has the main project code