# Queue Solution
```python
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        return self.items == []

    def enqueue(self, item):
        self.items.insert(0, item)

    def dequeue(self):
        return self.items.pop()

    def size(self):
        return len(self.items)

def ride_the_ride(queue):
    """
    The ride can sit 2 people at a time
    """
    while queue.size() > 1:
        person1 = queue.dequeue()
        person2 = queue.dequeue()
        print(person1, "and", person2, "are riding the ride")

people_queue = Queue()
people_queue.enqueue("John")
people_queue.enqueue("Mary")
people_queue.enqueue("Bob")
people_queue.enqueue("Sue")
print(people_queue.size())
ride_the_ride(people_queue)
print(people_queue.isEmpty())

"""
Expected output:
4
John and Mary are riding the ride
Bob and Sue are riding the ride
True
"""
```

# Linked List Solution
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

    def insert_tail(self, data):
        new_node = LinkedList.Node(data)
        if self.head is None:
            self.head = new_node
            self.tail = new_node
        else:
            new_node.prev = self.tail
            self.tail.next = new_node
            self.tail = new_node

    def insert_after(self, data, node):
        new_node = LinkedList.Node(data)
        if node is None:
            return
        new_node.next = node.next
        new_node.prev = node
        node.next.prev = new_node
        node.next = new_node

    def delete_head(self):
        self.head.next.prev = None
        self.head = self.head.next

    def delete_tail(self):
        self.tail.prev.next = None
        self.tail = self.tail.prev

    def delete_after(self, node):
        if node is None:
            return
        node.next = node.next.next
        node.next.prev = node

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
# Binary Search Tree Solution
```python
class BST:

    class Node:

        def __init__(self, data):
       
            self.data = data
            self.left = None
            self.right = None

    def __init__(self):

        self.root = None
#########
# This section of code allows us to display the tree in a for loop.

    def __iter__(self):

        yield from self._traverse_forward(self.root)  # Start at the root
        
    def _traverse_forward(self, node):

        if node is not None:
            yield from self._traverse_forward(node.left)
            yield node.data
            yield from self._traverse_forward(node.right)
#########
    def insert(self, data):

        if self.root is None:
            self.root = BST.Node(data)
        else:
            # Start at the root
            self._insert(data, self.root)  

    def _insert(self, data, node):
        # Notice how we use recursive to find a place to insert the data

        if node.data == data:
            return
        if data < node.data:
            # The data belongs on the left side.
            if node.left is None:
                # We found an empty spot
                node.left = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the left sub-tree.
                self._insert(data, node.left)
        else:
            # The data belongs on the right side.
            if node.right is None:
                # We found an empty spot
                node.right = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the right sub-tree.
                self._insert(data, node.right)
    
    def __contains__(self, data):
        
        return self._contains(data, self.root)  # Start at the root

    def _contains(self, data, node):
        
        if node is None:
            return False
        if node.data == data:
            return True
        if data < node.data:
            # The data belongs on the left side.
            return self._contains(data, node.left)
        else:
            # The data belongs on the right side.
            return self._contains(data, node.right)
    
tree = BST()
tree.insert(1)
tree.insert(2)
tree.insert(3)
for branch in tree:
    print(branch)

# Implement the contains function to see if the tree contains the data.
print(1 in tree)
print(4 in tree)
print(3 in tree)

# Expected Output:
# 1
# 2
# 3
# True
# False
# True
```
