# Stack

### Introduction to Stack Data Structure

A **stack** is a linear data structure that follows the **Last In, First Out (LIFO)** principle. The element added most recently is the first one to be removed. Think of a stack of plates: you add plates on top and remove the top plate first.

Key operations:

1. **Push**: Add an element to the stack.
2. **Pop**: Remove the top element.
3. **Peek**: View the top element without removing it.
4. **IsEmpty**: Check if the stack is empty.

### Python Implementation

Here's a simple implementation using a Python class:

```python
class Stack:
    def __init__(self):
        """Initialize an empty list to store stack elements."""
        self.stack = []

    def push(self, item):
        """Add an item to the top of the stack."""
        self.stack.append(item)  # Append adds the item to the end of the list.
        print(f"Pushed {item} onto the stack.")

    def pop(self):
        """
        Remove and return the top item of the stack.
        If the stack is empty, raise an exception.
        """
        if self.is_empty():
            raise IndexError("Pop from empty stack.")
        item = self.stack.pop()  # Remove and return the last item in the list.
        print(f"Popped {item} from the stack.")
        return item

    def peek(self):
        """
        Return the top item of the stack without removing it.
        If the stack is empty, raise an exception.
        """
        if self.is_empty():
            raise IndexError("Peek from empty stack.")
        return self.stack[-1]  # Access the last item in the list.

    def is_empty(self):
        """Check if the stack is empty."""
        return len(self.stack) == 0

    def size(self):
        """Return the number of items in the stack."""
        return len(self.stack)

# Example usage
if __name__ == "__main__":
    stack = Stack()
    stack.push(10)
    stack.push(20)
    stack.push(30)
    print(f"Top element: {stack.peek()}")  # Peek at the top element.
    print(f"Stack size: {stack.size()}")   # Check the stack size.
    stack.pop()                            # Remove the top element.
    print(f"Is stack empty? {stack.is_empty()}")  # Check if the stack is empty.
```

### Explanation

1. **Initialization (`__init__`)**: The stack is represented as a Python list.
2. **Push**: Uses `append` to add an item at the end of the list.
3. **Pop**: Uses `pop` to remove and return the last item.
4. **Peek**: Returns the last item without removing it.
5. **IsEmpty**: Checks if the stack has no elements.
6. **Size**: Returns the current number of elements in the stack.

This implementation is straightforward and uses Python's built-in list functionalities to manage the stack efficiently.
