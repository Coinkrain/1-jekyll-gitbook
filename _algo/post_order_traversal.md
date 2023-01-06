---
title: Post-order Traversal
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Post-order traversal is a tree traversal technique in which the left subtree is visited first, followed by the right subtree, and then the root node. It is often used to delete the tree or to release memory, as it allows the nodes to be processed after their children have been processed.

Here is an example of how to implement post-order traversal in JavaScript:

```js
function postOrder(node) {
  if (node === null) {
    return;
  }
  postOrder(node.left);
  postOrder(node.right);
  console.log(node.value);
}
```

In this example, the `postOrder` function takes a tree node as an argument and performs the post-order traversal of the tree starting from the given node. It prints the value of each node as it is visited. The function works by first traversing the left subtree, then traversing the right subtree, and finally visiting the root node.