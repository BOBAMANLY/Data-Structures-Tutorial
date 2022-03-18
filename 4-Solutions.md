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
