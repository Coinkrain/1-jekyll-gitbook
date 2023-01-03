---
title: Breadth First Tree
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


A breadth-first search (BFS) is an algorithm for traversing a tree or graph data structure. It explores the nodes at each level of the tree from left to right before moving on to the next level.

Here is an example of a function that performs a breadth-first search of a tree in JavaScript:

```js
function breadthFirstSearch(root, target) {
  const queue = [root];
  while (queue.length > 0) {
    const node = queue.shift();
    if (node.value === target) return true;
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }
  return false;
}
```

This function uses a queue to store the nodes to be visited, and explores the nodes at each level of the tree from left to right. It returns true if the target value is found, or false otherwise.

To use this function, you can pass in the root node of the tree and the target value as arguments:

```js
const tree = {
  value: 1,
  left: {
    value: 2,
    left: {
      value: 4,
      left: null,
      right: null
    },
    right: {
      value: 5,
      left: null,
      right: null
    }
  },
  right: {
    value: 3,
    left: {
      value: 6,
      left: null,
      right: null
    },
    right: {
      value: 7,
      left: null,
      right: null
    }
  }
};

const target = 6;
const found = breadthFirstSearch(tree, target);  // found = true
```

This function can be used to search for a specific value in a tree data structure.