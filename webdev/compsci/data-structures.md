Data Structures 

> This cheatsheet is written with python

Table of Contents
- [Linked List](#linked-list)
- [Stack](#stack)
- [Queue](#queue) 
- [Hash Table](#hash-table)
- [ ] Tree
- [ ] Graph
- [ ] Heap

## Linked List

```python
# A linked list is a sequence of data elements, which are connected together 
# via links. Each data element contains a connection to another data element 
# in form of a pointer
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current_node = self.head
        while current_node.next is not None:
            current_node = current_node.next
        current_node.next = new_node

    def prepend(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def delete(self, data):
        if self.head is None:
            return
        if self.head.data == data:
            self.head = self.head.next
            return
        current_node = self.head
        while current_node.next is not None:
            if current_node.next.data == data:
                current_node.next = current_node.next.next
                return
            current_node = current_node.next

    def print_list(self):
        current_node = self.head
        while current_node is not None:
            print(current_node.data)
            current_node = current_node.next

```

## Stack

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)
```

## Queue

```python
class Queue:
    def __init__(self):
        self.queue = []

    def enqueue(self, item):
        self.queue.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.queue.pop(0)

    def is_empty(self):
        return len(self.queue) == 0

    def size(self):
        return len(self.queue)

    def peek(self):
        if not self.is_empty():
            return self.queue[0]
```

## Hash Table

```python
class HashTable:
    def __init__(self):
        self.table = {}

    def put(self, key, value):
        self.table[key] = value

    def get(self, key):
        return self.table.get(key)

    def remove(self, key):
        if key in self.table:
            del self.table[key]

    def contains(self, key):
        return key in self.table

    def size(self):
        return len(self.table)

    def keys(self):
        return list(self.table.keys())

    def values(self):
        return list(self.table.values())
```
