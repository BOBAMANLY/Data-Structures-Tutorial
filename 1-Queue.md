# Queues

## Introduction

Have you ever had to stand in a line at a theme park and wait to get on a ride. A queue is that exact system, but integrated into software. You have a list or queue of items, and you intereact with each item in the order that they entered the list or queue. Queues are identified as first in first out.

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

## Common Terms
