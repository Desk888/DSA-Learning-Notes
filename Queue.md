# Queue

### Introduction to Queue Data Structure

A **queue** is a linear data structure that follows the **First In, First Out (FIFO)** principle. The element added first is the first one to be removed. Think of a queue of people waiting in line: the first person to join the queue is the first to leave.

Key operations:

1. **Enqueue**: Add an element to the rear of the queue.
2. **Dequeue**: Remove an element from the front of the queue.
3. **Peek**: View the front element without removing it.
4. **IsEmpty**: Check if the queue is empty.

### Python Implementation

Here’s a simple implementation using a Python class:

`class Queue:`
    `def __init__(self):`
        `"""Initialize an empty list to store queue elements."""`
        `self.queue = []`

    `def enqueue(self, item):`
        `"""Add an item to the rear of the queue."""`
        `self.queue.append(item)  # Append adds the item to the end of the list.`
        `print(f"Enqueued {item}.")`

    `def dequeue(self):`
        `"""`
        `Remove and return the front item of the queue.`
        `If the queue is empty, raise an exception.`
        `"""`
        `if self.is_empty():`
            `raise IndexError("Dequeue from empty queue.")`
        `item = self.queue.pop(0)  # Remove and return the first item in the list.`
        `print(f"Dequeued {item}.")`
        `return item`

    `def peek(self):`
        `"""`
        `Return the front item of the queue without removing it.`
        `If the queue is empty, raise an exception.`
        `"""`
        `if self.is_empty():`
            `raise IndexError("Peek from empty queue.")`
        `return self.queue[0]  # Access the first item in the list.`

    `def is_empty(self):`
        `"""Check if the queue is empty."""`
        `return len(self.queue) == 0`

    `def size(self):`
        `"""Return the number of items in the queue."""`
        `return len(self.queue)`
