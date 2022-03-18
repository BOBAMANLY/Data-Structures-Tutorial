# Queues

[Return to Welcome Page](0-Welcome.md)

## Introduction

Have you ever had to stand in a line at a theme park and wait to get on a ride. A queue is that exact system, but integrated into software. You have a list or queue of items, and you intereact with each item in the order that they entered the list or queue. Queues are identified as first in first out.

Keep these terms in mind:

Back of the Queue: Last item in the queue

Front of the Queue: First item in the queue

## Common Functions

In python we use the list method `pop()` in order to remove items from the queue at a certain position. `pop()` can take in one parameter, `pop(pos)`. It is the position of the item you want to remove. Keep in mind that `pop(pos)` also returns the value at pos. 

Normally, programmers will create methods called `enqueue(value)`, `dequeue()`, `size()`, and `empty()`.

### `Enqueue(value)`

This method is created to add values onto the back of the queue, putting them in line to be processed.

O(n) notation performance: O(1)

```python
my_queue = Queue()
my_queue.enqueue("John")
print(my_queue)
my_queue.enqueue("Jacob")
print(my_queue)
my_queue.enqueue("Smith")
print(my_queue)
```

### `Dequeue()`

This method will remove the item in the front of the queue. You do this once the item has been processed.

O(n) notation performance: O(n)

```python
my_queue.dequeue()
print(my_queue)
my_queue.dequeue()
print(my_queue)
my_queue.dequeue()
print(my_queue)
```

### `Size()`

This method will return the size of the queue.

O(n) notation performance: O(1)

```python
return len(my_queue)
```

### `Empty()`

This method will return True only if the queue is empty.

O(n) notation performance: O(1)

```python
if my_queue.size() == 0:
```

# Practice

This problem represents people riding a roller coaster. People enter the line and two people may ride the ride at a time. 

Your job is to make sure we can enqueue, dequeue, know if the line is empty, and see how many people are in line by implementing the `Queue()` functions.

```python
class Queue:
    def __init__(self):
        self.items = []

    def isEmpty(self):
        # Implement this function

    def enqueue(self, item):
        # Implement this function

    def dequeue(self):
        # Implement this function

    def size(self):
        # Implement this function

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

[Solution](4-Solutions.md)

