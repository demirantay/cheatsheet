# Sqlite - Python Driver

```python

import sqlite3
from sqlite3 import Error

try:
    conn = sqlite3.connect('example.db')
    
    # Once you have a Connection, you can create a Cursor object 
    # and call its execute() method to perform SQL commands:
    cur = con.cursor()

    # Create table
    cur.execute('''CREATE TABLE stocks
                   (date text, trans text, symbol text, qty real, price real)''')

    # Insert a row of data
    cur.execute("INSERT INTO stocks VALUES ('2006-01-05','BUY','RHAT',100,35.14)")
    
    # Save (commit) the changes
    con.commit()
except Error as e:
    print(e)
finally:
    if conn:
        # We can also close the connection if we are done with it.
        # Just be sure any changes have been committed or they will be lost.
        conn.close()
````
Usually your SQL operations will need to use values from Python variables. You shouldn’t assemble your query using Python’s string operations because doing so is insecure; it makes your program vulnerable to an SQL injection attack
```python
# Never do this -- insecure!
symbol = 'RHAT'
cur.execute("SELECT * FROM stocks WHERE symbol = '%s'" % symbol)
```

### Alternative to Python Variables

```python
# ...

# This is the qmark style:
cur.execute("insert into lang values (?, ?)", ("C", 1972))

# The qmark style used with executemany():
lang_list = [
    ("Fortran", 1957),
    ("Python", 1991),
    ("Go", 2009),
]
cur.executemany("insert into lang values (?, ?)", lang_list)

# And this is the named style:
cur.execute("select * from lang where first_appeared=:year", {"year": 1972})
print(cur.fetchall())

# ...
```
An SQL statement may use one of two kinds of placeholders: question marks (qmark style) or named placeholders (named style)
