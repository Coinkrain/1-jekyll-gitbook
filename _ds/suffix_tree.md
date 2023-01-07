---
title: Suffix tree
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A suffix tree is a tree-based data structure that is used to represent the suffixes of a string. It is a space-efficient data structure that allows you to perform efficient string searches and operations, such as finding the longest repeated substring, the longest common substring, and the shortest unique substrings.

In JavaScript, you can implement a suffix tree by creating a class or a constructor function that represents a node in the tree. Each node in the suffix tree has a value and a set of child nodes, and the child nodes represent the suffixes of the string.

Here is the full implementation of the `SuffixTreeNode` class:

```js
class SuffixTreeNode {
  constructor(value) {
    this.value = value;
    this.children = new Map();
  }
}
```

The `SuffixTreeNode` class has the following properties:

 - `value`: This is the value of the node, which represents a character in a string.
 - `children`: This is a map of child nodes, where the keys are the characters and the values are the child nodes.

Here is the full implementation of the `SuffixTree` class:

```js
class SuffixTree {
  constructor(string) {
    this.root = new SuffixTreeNode(null);
    this.string = string;
    for (let i = 0; i < string.length; i++) {
      this.insert(string.substring(i));
    }
  }

  insert(string) {
    let current = this.root;
    for (let i = 0; i < string.length; i++) {
      let char = string[i];
      if (!current.children.has(char)) {
        current.children.set(char, new SuffixTreeNode(char));
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

The `SuffixTree` class has the following methods:

 - `constructor(string)`: This is the constructor function for the SuffixTree class. It takes a string as an argument and creates a root node for the suffix tree. It also stores the string in the string property of the class. The insert method is called for each suffix of the string to insert the suffixes into the tree.
 - `insert(string)`: This method inserts a string into the suffix tree. It traverses the tree and adds a new node for each character in the string, starting at the root node.
 - `search(string)`: This method searches for a string in the suffix tree. It traverses the tree and returns true if the string is found, or false if the string is not found.
