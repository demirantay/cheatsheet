Data Structures 

> This cheatsheet is written with python

Table of Contents
- [Linked List](#linked-list)
- [ ] Doubly Linked List
- [ ] Queue
- [ ] Stack
- [ ] Hash Table
- [ ] Heap
- [ ] Tree (binary search, AVL, Red-black, Segment, Fenwick)
- [ ] Graph

## Linked List

```python
# A linked list is a sequence of data elements, which are connected together 
# via links. Each data element contains a connection to another data element 
# in form of a pointer
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None
```
