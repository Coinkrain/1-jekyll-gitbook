---
title: Radix tree
author: Subhahu
date: 2023-01-01
category: Data-Structure
layout: post
---


A radix tree (also known as a Patricia trie or a crit-bit tree) is a tree-based data structure that is used to store a set of strings in a space-efficient manner. It is a compressed trie, where each node represents a common prefix of the strings in the set.

In JavaScript, you can implement a radix tree by creating a class or a constructor function that represents a node in the tree. Each node in the radix tree has a value and a set of child nodes, and the child nodes represent the suffixes of the strings in the set.

Here is the full implementation of the `RadixTreeNode` class:

```js
class RadixTreeNode {
  constructor(value) {
    this.value = value;
    this.children = new Map();
  }
}
```

The RadixTreeNode class has the following properties:

 - `value`: This is the value of the node, which represents a character in a string.
 - `children`: This is a map of child nodes, where the keys are the characters and the values are the child nodes.


Here is the full implementation of the `RadixTree` class:

```js
class RadixTree {
  constructor() {
    this.root = new RadixTreeNode(null);
  }

  insert(string) {
    let current = this.root;
    for (let i = 0; i < string.length; i++) {
      let char = string[i];
      if (!current.children.has(char)) {
        current.children.set(char, new RadixTreeNode(char));
      }
      current = current.children.get(char);
    }
  }

  search(string) {
    let current = this.root;
    for (let i = 0; i < string.length; i++) {
      let char = string[i];
      if (!current.children.has(char)) {
        return false;
      }
      current = current.children.get(char);
    }
    return true;
  }
}
```

The `RadixTree` class has the following methods:

 - `insert(string)`: This method inserts a string into the radix tree. It traverses the tree and adds a new node for each character in the string, starting at the root node.
 - `search(string)`: This method searches for a string



 Here is an example of how to use the `RadixTree` class:

```js
let tree = new RadixTree();
tree.insert("hello");
tree.insert("world");
tree.insert("hi");
tree.insert("welcome");

console.log(tree.search("hello")); // true
console.log(tree.search("world")); // true
console.log(tree.search("hi")); // true
console.log(tree.search("welcome")); // true
console.log(tree.search("goodbye")); // false
```

In this example, we create a new `RadixTree` instance and insert four strings into the tree. We then search for the four strings and a string that is not in the tree, and print the results to the console.

