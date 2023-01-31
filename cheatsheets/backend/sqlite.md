# SQLite

Installing update
```
$ sudo apt install sqlite3
```
And to run the sqlite program you do
```
$ sqlite3
```
If you do not give a filename parameter then sqlite creates a temporary database, but if you give a filename it creates or connects to that database
```
$ sqlite3 dbName
```

## Special Commands

- `.help` -- lists all of the speical commands
- `.databases` -- list names and files of attached databases
- `.excel` -- Display the output of next command in spreadsheet
- `.quit` -- Exit this program
- `.mode` -- to switch between the output formats default output mode is "list"

## Changing Output Formats

The sqlite3 program is able to show the results of a query in 14 different formats:
- `ascii`, `csv`, `html`, `json`, `list`, `quote`, `tabs`, `box`, `column`, `insert`, `line`, `markdown`, `table`, `table`


Default
```
sqlite> .mode list
sqlite> select * from tbl1;
hello!|10
goodbye|20
sqlite>
```
Using the column type
```
sqlite> .mode column
sqlite> select * from tbl1;
one       two       
--------  ---
hello     10        
goodbye   20        
sqlite>
```
With markdown type
```
sqlite> .mode markdown
sqlite> select * from tbl1;
|   one   | two |
|---------|-----|
| hello!  | 10  |
| goodbye | 20  |
```

## Redirecting I/O

You can redirect the output from console to a file.
```
sqlite> .mode list
sqlite> .separator |
sqlite> .output test_file_1.txt
sqlite> select * from tbl1;
sqlite> .exit
$ cat test_file_1.txt
hello|10
goodbye|20
$
```

You can also read sql input text from a file.
```
sqlite> .read myscript.sql
```

You can export directly to excel instead of a file:
```
sqlite> .excel
sqlite> SELECT * FROM tab
```

## Accessing ZIP Archives As Database Files

Instead of files, you can read and write ZIP archives

```
CREATE TABLE zip(
  name,     // Name of the file
  mode,     // Unix-style file permissions
  mtime,    // Timestamp, seconds since 1970
  sz,       // File size after decompression
  rawdata,  // Raw compressed file data
  data,     // Uncompressed file content
  method    // ZIP compression method code
);
```

## Converting An Entire Database To An ASCII Text File

Use the ".dump" command to convert the entire contents of a database into a single ASCII text file.

```
$ sqlite3 ex1 .dump | gzip -c >ex1.dump.gz
```

> There are more commands to learn but this is sufficent enough for now
