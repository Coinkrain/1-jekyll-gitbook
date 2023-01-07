---
title: Union Find
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---



Union-find, also known as disjoint-set, is a data structure that tracks a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It supports two main operations: `find`, which returns the representative element (also known as the root) of the set that an element belongs to, and `union`, which merges two sets into a single set.

Here is an example of a simple union-find class in JavaScript:

```js
class UnionFind {
  constructor(size) {
    this.parent = new Array(size).fill(null).map((_, i) => i);
    this.size = new Array(size).fill(1);
  }

  find(x) {
    if (this.parent[x] !== x) {
      this.parent[x] = this.find(this.parent[x]);
    }
    return this.parent[x];
  }

  union(x, y) {
    let xRoot = this.find(x);
    let yRoot = this.find(y);
    if (xRoot === yRoot) {
      return;
    }
    if (this.size[xRoot] < this.size[yRoot]) {
      this.parent[xRoot] = yRoot;
      this.size[yRoot] += this.size[xRoot];
    } else {
      this.parent[yRoot] = xRoot;
      this.size[xRoot] += this.size[yRoot];
    }
  }
}
```

In this example, the `UnionFind` class has a constructor that initializes a new union-find data structure with a given size, and two methods: `find` and `union`. The `find` method returns the representative element of the set that an element belongs to, using path compression to improve the time complexity, and the `union` method merges two sets into a single set by updating the parent of one of the roots and adjusting the size of the resulting set.