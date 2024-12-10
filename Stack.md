# Stack

A **Stack** is a common data structure that follows the Last In, First Out (LIFO) principle. The element added last is the one to be removed. Think of a stack of plates: you add plates on the top and remove the top plate first. Stacks work the same.

 ## **Key Operations:**

- **Push**: Add an element to the top stack.
- **Pop**: Remove the top element.
- **Peek**: View the top element without removing it.
- **isEmpty** A method to check if the stack is empty.

Here's an implementation example of Stack class with all key operators in Python:

`class Stack:`
    `def __init__(self):`
        `"""Initialize an empty list to store stack elements."""`
        `self.stack = []`

    ``def push(self, item):``
        ``"""Add an item to the top of the stack."""``
        ``self.stack.append(item)  # Append adds the item to the end of the list.``
        ``print(f"Pushed {item} onto the stack.")``

    ``def pop(self):``
        ``"""``
        ``Remove and return the top item of the stack.``
        ``If the stack is empty, raise an exception.``
        ``"""``
        ``if self.is_empty():``
            ``raise IndexError("Pop from empty stack.")``
        ``item = self.stack.pop()  # Remove and return the last item in the list.``
        ``print(f"Popped {item} from the stack.")``
        ``return item``

    ``def peek(self):``
        ``"""``
        ``Return the top item of the stack without removing it.``
        ``If the stack is empty, raise an exception.``
        ``"""``
        ``if self.is_empty():``
            ``raise IndexError("Peek from empty stack.")``
        ``return self.stack[-1]  # Access the last item in the list.``

    ``def is_empty(self):``
        ``"""Check if the stack is empty."""``
        ``return len(self.stack) == 0``

    ``def size(self):``
        ``"""Return the number of items in the stack."""``
        ``return len(self.stack)``
