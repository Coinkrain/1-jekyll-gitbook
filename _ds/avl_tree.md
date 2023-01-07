---
title: AVL Tree
author: Subhahu
date: 2023-01-01
category: Data-Structure
layout: post
---


An AVL tree (named after its inventors Adelson-Velsky and Landis) is a self-balancing binary search tree. It is a data structure that allows you to store a sorted list of items efficiently, while maintaining the balance of the tree so that searches, insertions, and deletions can be performed in O(log n) time.

In JavaScript, you can implement an AVL tree by creating a class or a constructor function that represents a node in the tree. Each node can have up to two children, with the left child representing a node with a smaller value and the right child representing a node with a larger value. You can then use this node class to build the AVL tree by adding nodes for each item and maintaining the balance of the tree using rotations.

Here is an example of a simple AVL tree class in JavaScript:

```js
class AVLTreeNode {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
    this.height = 1;
  }
}

class AVLTree {
  constructor() {
    this.root = null;
  }

  insert(value) {
    this.root = this._insert(this.root, value);
  }

  _insert(node, value) {
    if (!node) {
      return new AVLTreeNode(value);
    }

    if (value < node.value) {
      node.left = this._insert(node.left, value);
    } else {
      node.right = this._insert(node.right, value);
    }

    node.height = 1 + Math.max(this._getHeight(node.left), this._getHeight(node.right));

    let balance = this._getBalance(node);

    // Left Left Case
    if (balance > 1 && value < node.left.value) {
      return this._rightRotate(node);
    }

    // Right Right Case
    if (balance < -1 && value > node.right.value) {
      return this._leftRotate(node);
    }

    // Left Right Case
    if (balance > 1 && value > node.left.value) {
      node.left = this._leftRotate(node.left);
      return this._rightRotate(node);
    }

    // Right Left Case
    if (balance < -1 && value < node.right.value) {
      node.right = this._rightRotate(node.right);
      return this._leftRotate(node);
    }

    return node;
  }

  _getHeight(node) {
    if (!node) return 0;
    return node.height;
  }

  _getBalance(node) {
    if (!node) return 0;
    return this._getHeight(node.left) - this._getHeight(node.right);
  }

  _leftRotate(node) {
    let newRoot = node.right;
    let temp = newRoot.left;

    newRoot.left = node;
    node.right = temp;

    node.height = 1 + Math.max(this._getHeight(node.left), this._getHeight(node.right));
    newRoot.height = 1 + Math.max(this._getHeight(newRoot.left), this._getHeight(newRoot.right));

    return newRoot;
  }

  _rightRotate(node) {
    let newRoot = node.left;
    let temp = newRoot.right;

    newRoot.right = node;
    node.left = temp;

    node.height = 1 + Math.max(this._getHeight(node.left), this._getHeight(node.right));
    newRoot.height = 1 + Math.max(this._getHeight(newRoot.left), this._getHeight(newRoot.right));

    return newRoot;
  }
}
```


