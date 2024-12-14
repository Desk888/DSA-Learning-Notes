# Red Black Tree

### What is a Red-Black Tree?

A **Red-Black Tree** is a self-balancing Binary Search Tree (BST) where every node has an additional color attribute: **red** or **black**. The tree enforces specific properties to ensure that it remains approximately balanced, making operations like search, insertion, and deletion run in \(O(\log n)\) time.

### Key Properties of Red-Black Trees:
1. Every node is either **red** or **black**.
2. The **root** of the tree is always **black**.
3. All **leaves** (NIL nodes) are black.
4. **Red nodes cannot have red children** (no two consecutive red nodes).
5. Every path from a node to its descendant NIL nodes must have the **same number of black nodes** (called the **black height**).

### Why Red-Black Trees?
These properties ensure that the longest path from the root to any leaf is at most twice as long as the shortest path, keeping the tree balanced.

---

### Python Implementation:
Here's a simplified implementation of a Red-Black Tree with insertion. Deletion can be added, but it's more complex.

```python
class Node:
    def __init__(self, key, color="red", left=None, right=None, parent=None):
        self.key = key
        self.color = color  # Red or Black
        self.left = left or None
        self.right = right or None
        self.parent = parent

class RedBlackTree:
    def __init__(self):
        self.NIL = Node(key=None, color="black")  # Sentinel NIL node
        self.root = self.NIL

    def insert(self, key):
        """Insert a new node with the given key."""
        new_node = Node(key, color="red", left=self.NIL, right=self.NIL)
        parent = None
        current = self.root

        # Standard BST insertion
        while current != self.NIL:
            parent = current
            if new_node.key < current.key:
                current = current.left
            else:
                current = current.right

        new_node.parent = parent
        if parent is None:  # New node is the root
            self.root = new_node
        elif new_node.key < parent.key:
            parent.left = new_node
        else:
            parent.right = new_node

        # Fix any violations of Red-Black properties
        self._fix_insert(new_node)

    def _fix_insert(self, node):
        """Restore Red-Black properties after insertion."""
        while node.parent and node.parent.color == "red":
            grandparent = node.parent.parent
            if node.parent == grandparent.left:
                uncle = grandparent.right
                # Case 1: Uncle is red
                if uncle and uncle.color == "red":
                    node.parent.color = "black"
                    uncle.color = "black"
                    grandparent.color = "red"
                    node = grandparent
                else:
                    # Case 2: Node is right child
                    if node == node.parent.right:
                        node = node.parent
                        self._rotate_left(node)
                    # Case 3: Node is left child
                    node.parent.color = "black"
                    grandparent.color = "red"
                    self._rotate_right(grandparent)
            else:
                uncle = grandparent.left
                # Symmetric to the above cases
                if uncle and uncle.color == "red":
                    node.parent.color = "black"
                    uncle.color = "black"
                    grandparent.color = "red"
                    node = grandparent
                else:
                    if node == node.parent.left:
                        node = node.parent
                        self._rotate_right(node)
                    node.parent.color = "black"
                    grandparent.color = "red"
                    self._rotate_left(grandparent)
        self.root.color = "black"

    def _rotate_left(self, node):
        """Perform a left rotation."""
        pivot = node.right
        node.right = pivot.left
        if pivot.left != self.NIL:
            pivot.left.parent = node
        pivot.parent = node.parent
        if node.parent is None:
            self.root = pivot
        elif node == node.parent.left:
            node.parent.left = pivot
        else:
            node.parent.right = pivot
        pivot.left = node
        node.parent = pivot

    def _rotate_right(self, node):
        """Perform a right rotation."""
        pivot = node.left
        node.left = pivot.right
        if pivot.right != self.NIL:
            pivot.right.parent = node
        pivot.parent = node.parent
        if node.parent is None:
            self.root = pivot
        elif node == node.parent.right:
            node.parent.right = pivot
        else:
            node.parent.left = pivot
        pivot.right = node
        node.parent = pivot

    def inorder(self, node=None):
        """In-order traversal of the tree."""
        if node is None:
            node = self.root
        if node != self.NIL:
            self.inorder(node.left)
            print(f"{node.key} ({node.color})", end=" ")
            self.inorder(node.right)

# Example usage
if __name__ == "__main__":
    rb_tree = RedBlackTree()
    values = [10, 20, 30, 15, 25, 5]
    for value in values:
        rb_tree.insert(value)
    
    print("In-order traversal of the Red-Black Tree:")
    rb_tree.inorder()
```

---

### Explanation:
1. **Node Class**:
   - Each node stores its `key`, `color`, pointers to `left`, `right`, and `parent`.
   - The `NIL` node acts as a sentinel leaf node to simplify tree operations.

2. **Insertion**:
   - Insert the node like in a BST.
   - Fix any violations of Red-Black properties using `_fix_insert`.

3. **Fix Insert**:
   - Recolor nodes and perform **rotations** (left or right) to ensure the tree remains balanced and follows all properties.

4. **Rotations**:
   - Used to adjust the structure of the tree during fixing.

---

This implementation focuses on **insertion**. Let me know if you'd like to extend it with deletion or additional explanations!
