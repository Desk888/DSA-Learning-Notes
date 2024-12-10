# Linked Lists

### Introduction to Linked List Data Structure

A **linked list** is a linear data structure consisting of nodes, where each node contains two parts:

1. **Data**: The value stored in the node.
2. **Next**: A reference (or pointer) to the next node in the sequence.

Unlike arrays, linked lists do not store elements in contiguous memory locations, making insertions and deletions more efficient. The most common types are:

- **Singly Linked List**: Each node points to the next node.
- **Doubly Linked List**: Each node points to both the next and the previous node.

### Python Implementation of a Singly Linked List

Here’s a basic implementation:

```python
class Node:
    def __init__(self, data):
        """Initialize a node with data and a pointer to the next node."""
        self.data = data
        self.next = None  # By default, the next pointer is None.

class LinkedList:
    def __init__(self):
        """Initialize an empty linked list."""
        self.head = None  # The head points to the first node.

    def append(self, data):
        """
        Add a node with the given data to the end of the list.
        If the list is empty, the new node becomes the head.
        """
        new_node = Node(data)
        if not self.head:  # If the list is empty.
            self.head = new_node
            print(f"Added {data} as the head node.")
            return
        current = self.head
        while current.next:  # Traverse to the last node.
            current = current.next
        current.next = new_node  # Link the last node to the new node.
        print(f"Appended {data} to the linked list.")

    def display(self):
        """Print all nodes in the list."""
        if not self.head:
            print("The linked list is empty.")
            return
        current = self.head
        print("Linked List:", end=" ")
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")  # End of the list.

    def delete(self, data):
        """
        Delete the first node containing the given data.
        If the data is not found, do nothing.
        """
        if not self.head:
            print("The linked list is empty. Nothing to delete.")
            return
        if self.head.data == data:  # If the head node is to be deleted.
            self.head = self.head.next
            print(f"Deleted {data} from the linked list.")
            return
        current = self.head
        while current.next and current.next.data != data:  # Traverse to find the node.
            current = current.next
        if current.next:  # If the data is found.
            current.next = current.next.next
            print(f"Deleted {data} from the linked list.")
        else:
            print(f"{data} not found in the linked list.")

# Example usage
if __name__ == "__main__":
    ll = LinkedList()
    ll.append(10)
    ll.append(20)
    ll.append(30)
    ll.display()  # Display the linked list.
    ll.delete(20) # Delete a node with value 20.
    ll.display()  # Display the updated list.
```

### Explanation

1. **Node Class**: Represents an individual node with `data` and a `next` pointer.
2. **LinkedList Class**:
    - **Append**: Adds a new node at the end of the list.
    - **Display**: Traverses and prints all nodes in the list.
    - **Delete**: Finds and removes the first node containing the specified value.
3. **Head Pointer**: Points to the first node, and the list is traversed starting from `head`.

This is a basic singly linked list. In real-world applications, you might want to implement additional methods for searching, inserting at specific positions, or reversing the list.
