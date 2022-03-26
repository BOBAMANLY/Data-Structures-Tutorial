# Linked Lists

[Return to Welcome Page](0-Welcome.md)

## Introduction

A Linked List is a very interesting data structure. This is because it is not built the same as a normal list or array. It uses pointers to link nodes together, creating the link. 

A node is the object, a pointer tells us what the next node is. A double linked list has pointers pointing forward and backward allowing us to iterate forwards and backwards.

##Structure

{Head} --> {Node 1: data}{pointer} --> {Node 2: data}{pointer} --> null

## Common Functions

The term `Head` refers to the first node in the linked list.

The last item or `Tail` has a pointer that returns `None`, meaning there are no more nodes in the list.

### `new_node(value)`

To add a new node, we have to know where we are adding it. We can add nodes to the beginning, end, or middle of a linked list.

O(n) notation performance: O(1)

####Empty list

A special case happens if the linked list is empty. We simply add a node and set the pointers.

```python
def new_node(self, value):
    new_node = Node(value)
    self.tail = new_node
    self.head = new_node
```

####Beginning

To add a node to the beginning, we simply change the head to point to the new node, and the new node pointer will point to the now second node.

```python
def insert_head(self, value):
    new_node = Node(value)
    new_node.next = self.head
    self.head.prev = new_node
    self.head = new_node
```

####Middle

While adding a node to the middle of a linked list, we must change the pointers of the previous node and the next node.

```python
def insert_middle(self, current_node, value):
    new_node = Node(value)
    new_node.next = current_node.next
    current_node.next.prev = new_node
    new_node.prev = current_node
    current_node.next = new_node
```

####End

Adding to the end of a list only requires us to change the last nodes pointers and set the new node as teh tail.

```python
def insert_end(self, value):
    new_node = Node(value)
    new_node.prev = self.tail
    self.tail.next = new_node
    self.tail = new_node
```

### `delete_node(value)`

While deleting nodes, we have the same rules as adding nodes. It is all about changing the pointers.

O(n) notation performance: O(1)

####Remove Head
```python
def remove_head(self):
    self.head.next.prev = None
    self.head = self.head.next
```

####Remove Tail
```python
def remove_tail(self):
    self.tail.prev.next = None
    self.tail = self.tail.prev
```

####Remove Middle
```python
def remove_middle(self, current_node)
    current_node.next.prev = current_node.prev
    current_node.prev.next = current_node.next
```

##Display a linked list

There are a few ways to display a linked list. We can't use a normal for loop and display each item. We have to use a while loop.

We iterate through each item by follwing the pointers and displaying their information at each node.

```python
def display_linked_list(self):
    current = self.head
    while current:
        print(current.data, end=" ")
        current = current.next
    print()
```

## Example

```python
class LinkedList:
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None
            self.prev = None
    def __init__(self):
        self.head = None
        self.tail = None

    def insert_head(self, data):
        new_node = LinkedList.Node(data)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.next = self.head
            self.head.prev = new_node
            self.head = new_node

    def display_linked_list(self):
        current = self.head
        while current:
            print(current.data, end="\n")
            current = current.next
        print()


def main():
    linked_list = LinkedList()
    linked_list.insert_head("John")
    linked_list.insert_head("Jane")
    linked_list.insert_head("Jack")
    linked_list.display_linked_list()

    """
    Output:
    Jack
    Jane
    John
    """
main()
```

# Practice

```python
class LinkedList:
    class Node:
        def __init__(self, data):
            self.data = data
            self.next = None
            self.prev = None
    def __init__(self):
        self.head = None
        self.tail = None

    def insert_head(self, data):
        # Implement this function
        pass

    def insert_tail(self, data):
        # Implement this function
        pass

    def insert_after(self, data, node):
        # Implement this function
        pass

    def delete_head(self):
        # Implement this function
        pass

    def delete_tail(self):
        # Implement this function
        pass

    def delete_after(self, node):
        # Implement this function
        pass
    
    def display_linked_list(self):
        current = self.head
        while current:
            print(current.data, end="\n")
            current = current.next
        print()


def main():
    linked_list = LinkedList()
    linked_list.insert_head("John")
    linked_list.insert_head("Jane")
    linked_list.insert_head("Jack")
    linked_list.display_linked_list()
    linked_list.insert_tail("Jill")
    linked_list.display_linked_list()
    linked_list.insert_after("Jana", linked_list.head.next)
    linked_list.display_linked_list()
    linked_list.delete_head()
    linked_list.display_linked_list()
    linked_list.delete_tail()
    linked_list.display_linked_list()
    linked_list.delete_after(linked_list.head)
    linked_list.display_linked_list()

    """
    Output:
    Jack
    Jane
    John
        
    Jack
    Jane
    John
    Jill

    Jack
    Jane
    Jana
    John
    Jill

    Jane
    Jana
    John
    Jill

    Jane
    Jana
    John

    Jane
    John
    """

main()
```

[Solution](4-Solutions.md)

