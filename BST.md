# Binary Search Tree

### Introduction to Binary Tree Data Structure

A **binary tree** is a hierarchical data structure where each node has at most two children, referred to as the **left child** and the **right child**. It is commonly used for searching, sorting, and hierarchical data representation.

Key Terms:

1. **Root**: The topmost node in the tree.
2. **Leaf**: A node with no children.
3. **Height**: The length of the longest path from the root to a leaf.
4. **Binary Search Tree (BST)**: A binary tree where the left child contains values less than the parent, and the right child contains values greater than the parent.

### Python Implementation of a Binary Tree

Here’s a basic implementation:

```python
class Node:
    def __init__(self, value):
        """Initialize a node with a value and pointers to left and right children."""
        self.value = value
        self.left = None  # Pointer to the left child.
        self.right = None  # Pointer to the right child.

class BinaryTree:
    def __init__(self):
        """Initialize an empty binary tree."""
        self.root = None

    def insert(self, value):
        """
        Insert a value into the binary tree.
        Follows level-order insertion for simplicity.
        """
        new_node = Node(value)
        if not self.root:  # If the tree is empty, the new node becomes the root.
            self.root = new_node
            print(f"Inserted {value} as the root node.")
            return
        queue = [self.root]  # Use a queue for level-order traversal.
        while queue:
            current = queue.pop(0)  # Dequeue the front node.
            if not current.left:  # Insert as the left child if it's empty.
                current.left = new_node
                print(f"Inserted {value} as the left child of {current.value}.")
                return
            else:
                queue.append(current.left)  # Add the left child to the queue.
            if not current.right:  # Insert as the right child if it's empty.
                current.right = new_node
                print(f"Inserted {value} as the right child of {current.value}.")
                return
            else:
                queue.append(current.right)  # Add the right child to the queue.

    def inorder_traversal(self, node):
        """Perform in-order traversal (Left, Root, Right)."""
        if node:
            self.inorder_traversal(node.left)  # Visit left child.
            print(node.value, end=" ")  # Visit root.
            self.inorder_traversal(node.right)  # Visit right child.

# Example usage
if __name__ == "__main__":
    tree = BinaryTree()
    tree.insert(10)
    tree.insert(20)
    tree.insert(30)
    tree.insert(40)
    tree.insert(50)
    print("In-order Traversal:", end=" ")
    tree.inorder_traversal(tree.root)  # Display the tree in in-order.
    print()
```

### Explanation

1. **Node Class**: Represents an individual node with a `value` and pointers to its `left` and `right` children.
2. **BinaryTree Class**:
    - **Insert**: Inserts a new value into the tree using level-order (breadth-first) traversal.
    - **In-order Traversal**: Recursively traverses the tree in left-root-right order.
3. **Root Pointer**: Points to the root node, from where the tree traversal begins.

This example implements level-order insertion and in-order traversal. You can extend it with other traversal methods (pre-order, post-order) or specific tree operations like searching, deleting, and balancing.
