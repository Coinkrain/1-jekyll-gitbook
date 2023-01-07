---
title: Binary Search Tree
author: Subhahu Jain
date: 2019-05-30
category: Data-Structure
layout: post
---


A binary search tree (BST) is a type of binary tree that is commonly used to store data in a sorted and searchable manner. In a BST, each node has a value that is greater than or equal to the values of its left children and less than or equal to the values of its right children. This property allows the tree to be searched efficiently, as it is possible to narrow down the search to a specific subtree by comparing the target value to the value of the current node.

Here is an example of a simple BST class in JavaScript:

```js
class BST {
  constructor() {
    this.root = null;
  }

  insert(value) {
    let newNode = { value, left: null, right: null };
    if (this.root === null) {
      this.root = newNode;
    } else {
      let current = this.root;
      while (true) {
        if (value < current.value) {
          if (current.left === null) {
            current.left = newNode;
            break;
          } else {
            current = current.left;
          }
        } else {
          if (current.right === null) {
            current.right = newNode;
            break;
          } else {
            current = current.right;
          }
        }
      }
    }
  }

  search(value) {
    let current = this.root;
    while (current) {
      if (value === current.value) {
        return true;
      } else if (value < current.value) {
        current = current.left;
      } else {
        current = current.right;
      }
    }
    return false;
  }
}
```

In this example, the `BST` class has a constructor that initializes an empty tree, and two methods: `insert` and `search`. The `insert` method adds a new node to the tree with the given value, and the `search` method searches for a node with the given value and returns `true` if it is found, or `false` otherwise.

