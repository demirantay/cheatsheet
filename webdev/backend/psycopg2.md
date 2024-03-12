# Psycopg2 

This cheatsheet is about the psycopg2 packet.

Installation:
```
$ pip install psycopg2
```
install dev tools for ubuntu
```
$ sudo apt install -y build-essential libssl-dev libffi-dev python3-dev
```

# Python Usage

Details Postgres:
- `Username`: The username you use to work with PostgreSQL, The default username for the PostgreSQL database is Postgres.
- `Password`: Password is given by the user at the time of installing the PostgreSQL.
- `Host Name`: This is the server name or Ip address on which PostgreSQL is running. if you are running on localhost, then you can use localhost, or its IP, i.e., 127.0.0.0
- `Database Name`: Database name to which you want to connect. Here we are using Database named “postgres_db“.

<br>

How to Connect to PostgreSQL in Python:
- `connect()` -- used to connect to postgresql db
- `cursor()` -- Create a cursor object using the connection object returned by the connect method to execute PostgreSQL queries from Python.
- `execute()` -- run the SQL query and return the result.
- `fetchall()`, `fetchone`, `fetchmany` -- to read query results
- `cursor.close()` -- close the cursor
- `connection.close()` -- close the connection

Example:
```python
import psycopg2
from psycopg2 import Error

try:
    # Connect to an existing database
    connection = psycopg2.connect(user="postgres",
                                  password="pynative@#29",
                                  host="127.0.0.1",
                                  port="5432",
                                  database="postgres_db")

    # Create a cursor to perform database operations
    cursor = connection.cursor()
    
    # Print PostgreSQL details
    print("PostgreSQL server information")
    print(connection.get_dsn_parameters(), "\n")
    
    # Executing a SQL query
    cursor.execute("SELECT version();")
    
    # Fetch result
    record = cursor.fetchone()
    print("You are connected to - ", record, "\n")

except (Exception, Error) as error:
    print("Error while connecting to PostgreSQL", error)
finally:
    if (connection):
        cursor.close()
        connection.close()
        print("PostgreSQL connection is closed")
```
OUTPUT
```
PostgreSQL server information
{'user': 'postgres', 'dbname': 'python_db', 'host': '127.0.0.1', 'port': '5432', 'tty': '', 'options': '', 'sslmode': 'prefer', 'sslcompression': '0', 'krbsrvname': 'postgres', 'target_session_attrs': 'any'} 

You are connected to -  ('PostgreSQL 12.2) 
PostgreSQL connection is closed
```

<br>


### More Advanced Usage

Lets see another exmpale with more SQL queries:
```python
import psycopg2

try:
    connection = psycopg2.connect(user="postgres",
                                  password="pynative@#29",
                                  host="127.0.0.1",
                                  port="5432",
                                  database="postgres_db")

    cursor = connection.cursor()
    # Executing a SQL query to insert data into  table
    insert_query = """ INSERT INTO mobile (ID, MODEL, PRICE) VALUES (1, 'Iphone12', 1100)"""
    cursor.execute(insert_query)
    connection.commit()
    print("1 Record inserted successfully")
    # Fetch result
    cursor.execute("SELECT * from mobile")
    record = cursor.fetchall()
    print("Result ", record)

    # Executing a SQL query to update table
    update_query = """Update mobile set price = 1500 where id = 1"""
    cursor.execute(update_query)
    connection.commit()
    count = cursor.rowcount
    print(count, "Record updated successfully ")
    # Fetch result
    cursor.execute("SELECT * from mobile")
    print("Result ", cursor.fetchall())

    # Executing a SQL query to delete table
    delete_query = """Delete from mobile where id = 1"""
    cursor.execute(delete_query)
    connection.commit()
    count = cursor.rowcount
    print(count, "Record deleted successfully ")
    # Fetch result
    cursor.execute("SELECT * from mobile")
    print("Result ", cursor.fetchall())


except (Exception, psycopg2.Error) as error:
    print("Error while connecting to PostgreSQL", error)
finally:
    if connection:
        cursor.close()
        connection.close()
        print("PostgreSQL connection is closed")
```

