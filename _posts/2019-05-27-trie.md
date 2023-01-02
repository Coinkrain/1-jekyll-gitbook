---
title: Trie
author: Subhahu Jain
date: 2019-04-27
category: Data-Structure
layout: post
---


A Trie (also known as a prefix tree) is a special kind of tree data structure that is used to store an associative array where the keys are sequences (usually strings). It allows you to search for a key efficiently, as well as to insert and delete keys.

In JavaScript, you can implement a Trie by creating a class or a constructor function that represents a node in the Trie. Each node can have multiple children, with each child representing a single character in the key. You can then use this node class to build the Trie by adding nodes for each character in the key, and linking the nodes together to form the tree structure.

Here is an example of a simple Trie class in JavaScript:

```js
class TrieNode {
  constructor() {
    this.children = {};
    this.isEnd = false;
  }
}

class Trie {
  constructor() {
    this.root = new TrieNode();
  }

  insert(word) {
    let current = this.root;

    for (let i = 0; i < word.length; i++) {
      let char = word[i];
      if (!current.children[char]) {
        current.children[char] = new TrieNode();
      }
      current = current.children[char];
    }

    current.isEnd = true;
  }

  search(word) {
    let current = this.root;

    for (let i = 0; i < word.length; i++) {
      let char = word[i];
      if (!current.children[char]) {
        return false;
      }
      current = current.children[char];
    }

    return current.isEnd;
  }
}

let trie = new Trie();
trie.insert("apple");
console.log(trie.search("apple"));  // Output: true
console.log(trie.search("app"));    // Output: false
```

In this example, the TrieNode class represents a node in the Trie, and the Trie class represents the Trie itself. The insert method is used to add a new key to the Trie, and the search method is used to search for a key in the Trie.

