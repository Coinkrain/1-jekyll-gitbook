---
title: Binary Tree
author: Subhahu Jain
date: 2019-04-29
category: Data-Structure
layout: post
---

A binary tree is a tree data structure in which each node has at most two children. Here is an example of a binary tree class in JavaScript:

```js
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}
```

To create a binary tree, you can create a new instance of the BinaryTree class and assign its left and right children using the left and right properties:

```js
const root = new BinaryTree(1);
root.left = new BinaryTree(2);
root.right = new BinaryTree(3);
root.left.left = new BinaryTree(4);
root.left.right = new BinaryTree(5);
root.right.left = new BinaryTree(6);
root.right.right = new BinaryTree(7);
```

This creates the following binary tree:

```
      1
    /   \
   2     3
  / \   / \
 4   5 6   7
 ```
 
You can traverse a binary tree using different tree traversal algorithms, such as depth-first search (DFS) or breadth-first search (BFS). Here is an example of a DFS traversal using in-order traversal (left-root-right):

```js
function inOrderTraversal(root) {
  if (!root) return;
  inOrderTraversal(root.left);
  console.log(root.value);
  inOrderTraversal(root.right);
}
```

You can call this function on the root node of the binary tree to perform an in-order traversal:

```js
inOrderTraversal(root);
```

This will print the values of the nodes in the following order: 4, 2, 5, 1, 6, 3, 7.
