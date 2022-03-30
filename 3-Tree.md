# Binary Search Trees

[Return to Welcome Page](0-Welcome.md)

## Introduction

A Binary Search Tree is very similar to linked lists. However each node can hold a maximum of 2 child nodes. The data is organized by comparing the new node with the parent nodes. Items that are "less" than the parent go to the left while items that are "greater than the parent go to the right. This type of tree has a O(log n) performance.

### Example Tree
```
        20
      /    \
   14        28
  /  \      /  \
10   17    23   30
```

When all the items are lined up going down one "branch", the tree is actually the same as a linked list. While searching for values in this type of tree, it has O(n) performance.

### Tree as Linked List
20
  \
   23
     \
      26
        \
         29
         
A Binary Search Tree is all about data comparison. To find where to place a node, or "leaf", is by comparing the new node to the parent, and moving down the tree until you find an empty spot.

## Recursion

Recursion is the idea of breaking a problem up into smaller portions. It is similar to solving a maze. We walk down the paths and when we find a dead end, we turn around and go down the next path. It is a systematic way to go through a problem until the solution is found. 

Here is an example of recusion.
```python
def repeat():
    print("Do it again")
    repeat()
repeat()
```
This function will call itself over and over until we hit the recursion limit. The recursion limit is in place as a saftey for code that runs infinitly or too many times.

To use recursion we need an end case and for the problem to be solvable by getting smaller.
```python
def repeat(this_many_times):
    if this_many_times == 0:
        return 1
    else:
        print("Do it again")
        return repeat(this_many_times - 1)
repeat(5)
```
This code will run until the variable `this_many_times` hits 0.

There is a way to avoid recursive calls that are repetitive through memoization.
Here is an example.
```python
def repeat(this_many_times, printed_statements = Null):
    if this_many_times == 0:
        return 1
    else:
        if printed_statements == "Do it again":
            return 1
        else:
            print("Do it again")
            printed_statements = "Do it again"
            return repeat(this_many_times - 1, printed_statements)
repeat(5)
```
We send a variable that can prevent an action if the action is a repeat of a previous recursive call.

## Common Methods

insert(value)	Insert a value into the tree.	O(log n) - Recursively search the subtrees to find the next available spot
remove(value)	Remove a value from the tree.	O(log n) - Recursively search the subtrees to find the value and then remove it. This will require some cleanup of the adjacent nodes.
contains(value)	Determine if a value is in the tree.	O(log n) - Recursively search the subtrees to find the value.
traverse_forward	Visit all objects from smallest to largest.	O(n) - Recursively traverse the left subtree and then the right subtree.
traverse_reverse	Visit all objects from largest to smallest.	O(n) - Recursively traverse the right subtree and then the left subtree.
height(node)	Determine the height of a node. If the height of the tree is needed, the root node is provided.	O(n) - Recursively find the height of the left and right subtrees and then return the maximum height (plus one to account for the root).
size()	Return the size of the BST.	O(1) - The size is maintained within the BST class.
empty()	Returns true if the root node is empty. This can also be done by checking the size for 0.	O(1) - The comparison of the root node or the size.

## Example

```python

```

# Practice

```python

```

[Solution](4-Solutions.md)
