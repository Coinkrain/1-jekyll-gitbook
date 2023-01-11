---
title: Depth First Tree
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



A depth-first search (DFS) is an algorithm for traversing a tree or graph data structure. It starts at the root node and explores as far as possible along each branch before backtracking.

Here is an example of a function that performs a depth-first search of a tree in JavaScript:

```js
function depthFirstSearch(root, target) {
  if (root === null) return false;
  if (root.value === target) return true;
  return depthFirstSearch(root.left, target) || depthFirstSearch(root.right, target);
}
```

This function uses a recursive approach to explore the left and right subtrees of the root node, and returns true if the target value is found, or false otherwise.

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
const found = depthFirstSearch(tree, target);  // found = true
```

This function can be used to search for a specific value in a tree data structure.