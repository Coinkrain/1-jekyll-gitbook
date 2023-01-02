---
title: Red-black tree
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A red-black tree is a self-balancing binary search tree. It is a data structure that allows you to store a sorted list of items efficiently, while maintaining the balance of the tree so that searches, insertions, and deletions can be performed in O(log n) time.

In JavaScript, you can implement a red-black tree by creating a class or a constructor function that represents a node in the tree. Each node can have up to two children, with the left child representing a node with a smaller value and the right child representing a node with a larger value. Each node also has a color, which can be either red or black. You can then use this node class to build the red-black tree by adding nodes for each item and maintaining the balance of the tree using rotations and color changes.

The RedBlackTree class is a data structure that represents a red-black tree, which is a self-balancing binary search tree. It allows you to store a sorted list of items efficiently, while maintaining the balance of the tree so that searches, insertions, and deletions can be performed in O(log n) time.

Here is a list of the methods that are implemented in the RedBlackTree class:

constructor(): This is the constructor function for the RedBlackTree class. It initializes an empty tree with a null root node.

insert(value): This method inserts a new node with the specified value into the tree. It first creates a new RedBlackTreeNode object with the value and a color of red. Then it inserts the node into the tree by traversing the tree and finding the correct position for the new node based on its value. Finally, it calls the _fixInsert method to restore the balance of the tree after the insertion.

_fixInsert(node): This method is used to fix the balance of the tree after inserting a new node. It starts at the new node and works its way up the tree, checking the balance at each node. If the new node's parent is red (which means the tree is unbalanced), it performs rotations and color changes to restore the balance of the tree.

_rotateLeft(node): This method performs a left rotation on the tree at the specified node. It rearranges the nodes in the tree so that the specified node becomes the right child of its left child, and its left child becomes the parent of the specified node.

_rotateRight(node): This method performs a right rotation on the tree at the specified node. It rearranges the nodes in the tree so that the specified node becomes the left child of its right child, and its right child becomes the parent of the specified node.



Here is an example of a simple red-black tree class in JavaScript:

essage:

```js
class RedBlackTreeNode {
  constructor(value, color) {
    this.value = value;
    this.left = null;
    this.right = null;
    this.parent = null;
    this.color = color;
  }
}

class RedBlackTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    let newNode = new RedBlackTreeNode(value, "red");

    if (!this.root) {
      this.root = newNode;
      newNode.color = "black";
      return;
    }

    let current = this.root;
    while (true) {
      if (value < current.value) {
        if (!current.left) {
          current.left = newNode;
          newNode.parent = current;
          this._fixInsert(newNode);
          break;
        } else {
          current = current.left;
        }
      } else {
        if (!current.right) {
          current.right = newNode;
          newNode.parent = current;
          this._fixInsert(newNode);
          break;
        } else {
          current = current.right;
        }
      }
    }
  }

_fixInsert(node) {
  while (node.parent && node.parent.color === "red") {
    let uncle = null;
    if (node.parent === node.parent.parent.left) {
      uncle = node.parent.parent.right;
      if (uncle && uncle.color === "red") {
        node.parent.color = "black";
        uncle.color = "black";
        node.parent.parent.color = "red";
        node = node.parent.parent;
        continue;
      }
      if (node === node.parent.right) {
        node = node.parent;
        this._rotateLeft(node);
      }
      node.parent.color = "black";
      node.parent.parent.color = "red";
      this._rotateRight(node.parent.parent);
    } else {
      uncle = node.parent.parent.left;
      if (uncle && uncle.color === "red") {
        node.parent.color = "black";
        uncle.color = "black";
        node.parent.parent.color = "red";
        node = node.parent.parent;
        continue;
      }
      if (node === node.parent.left) {
        node = node.parent;
        this._rotateRight(node);
      }
      node.parent.color = "black";
      node.parent.parent.color = "red";
      this._rotateLeft(node.parent.parent);
    }
  }
  this.root.color = "black";
}


_rotateLeft(node) {
  let right = node.right;
  node.right = right.left;
  if (right.left) {
    right.left.parent = node;
  }
  right.parent = node.parent;
  if (!node.parent) {
    this.root = right;
  } else if (node === node.parent.left) {
    node.parent.left = right;
  } else {
    node.parent.right = right;
  }
  right.left = node;
  node.parent = right;
}



_rotateRight(node) {
  let left = node.left;
  node.left = left.right;
  if (left.right) {
    left.right.parent = node;
  }
  left.parent = node.parent;
  if (!node.parent) {
    this.root = left;
  } else if (node === node.parent.right) {
    node.parent.right = left;
  } else {
    node.parent.left = left;
  }
  left.right = node;
  node.parent = left;
}


}
        
```

