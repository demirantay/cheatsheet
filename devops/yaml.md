## Yaml

> Yaml cheatsheet

YAML (YAML Ain’t Markup Language) is a human-readable data format often used for configuration files.

Key Characteristics:
- `Indentation-based`: Similar to Python, indentation is critical. Levels of indentation define hierarchy.
- `Key-Value Pairs`: Data is stored as key-value pairs (key: value).
- `Data types`: Supports strings, numbers, lists, and dictionaries.

exmaple of a YAML
```yaml
name: John Doe
age: 30
languages:
  - Python
  - JavaScript
  - Java
address:
  street: 123 Elm St
  city: Springfield
  zip: 12345
```
Explanation:

- `name` and `age` are simple key-value pairs.
- `languages` is a list.
- `address` is a nested dictionary.

How to Write YAML Files:
- Use spaces (not tabs) for indentation. (2 spaces)
- Start with a key followed by a colon (`:`), and add the corresponding value.
- Lists are created using hyphens (`-`).
