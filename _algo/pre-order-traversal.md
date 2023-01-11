---
title: Pre-Order Traversal
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Pre-order traversal is a tree traversal technique in which the root node is visited first, followed by the left subtree, and then the right subtree. It is often used to implement expressions in infix notation, as it allows the operator to be processed between the operands.

Here is an example of how to implement pre-order traversal in JavaScript:

```js
function preOrder(node) {
  if (node === null) {
    return;
  }
  console.log(node.value);
  preOrder(node.left);
  preOrder(node.right);
}
```

In this example, the `preOrder` function takes a tree node as an argument and performs the pre-order traversal of the tree starting from the given node. It prints the value of each node as it is visited. The function works by first visiting the root node, then traversing the left subtree, and finally traversing the right subtree.