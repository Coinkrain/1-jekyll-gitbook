---
title: Fenwick Tree
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---



A Fenwick tree, also known as a binary indexed tree, is a data structure that allows for efficient calculation and modification of prefix sums in an array. It works by representing the array as a tree, where each node stores the sum of the values in its subtree, and the parent of a node at index i is the node at index i & -i, which is the least significant 1-bit in the binary representation of i.

Here is an example of a simple Fenwick tree class in JavaScript:

```js
class FenwickTree {
  constructor(arr) {
    this.tree = new Array(arr.length + 1).fill(0);
    for (let i = 0; i < arr.length; i++) {
      this.update(i, arr[i]);
    }
  }

  update(index, value) {
    index++;
    while (index < this.tree.length) {
      this.tree[index] += value;
      index += index & -index;
    }
  }

  query(index) {
    let sum = 0;
    index++;
    while (index > 0) {
      sum += this.tree[index];
      index -= index & -index;
    }
    return sum;
  }
}
```

In this example, the `FenwickTree` class has a constructor that initializes a new Fenwick tree with a given array of values, and two methods: `update` and `query`. The `update` method modifies the value at a given index in the original array and updates the tree accordingly, and the `query` method returns the sum of the values in the original array up to a given index.