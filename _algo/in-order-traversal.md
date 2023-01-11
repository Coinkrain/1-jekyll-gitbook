---
title: In Order Traversal
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


In-order traversal is a tree traversal technique in which the left subtree is visited first, followed by the root node, and then the right subtree. It is often used to implement expressions in prefix notation, as it allows the operator to be processed after the operands.

Here is an example of how to implement in-order traversal in JavaScript:

```js
function inOrder(node) {
  if (node === null) {
    return;
  }
  inOrder(node.left);
  console.log(node.value);
  inOrder(node.right);
}
```

In this example, the `inOrder` function takes a tree node as an argument and performs the in-order traversal of the tree starting from the given node. It prints the value of each node as it is visited. The function works by first traversing the left subtree, then visiting the root node, and finally traversing the right subtree.