---
title: Disjoint Set
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---



A disjoint set (also known as a union-find set) is a data structure that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It allows you to efficiently find out which subset a particular element is in and whether two elements are in the same subset.

In JavaScript, you can implement a disjoint set using a class or a constructor function. The class should have a method to add elements to the set, a method to find the subset that an element belongs to, and a method to unite two subsets into a single subset.

Here is an example of a simple disjoint set class in JavaScript:

```js
class DisjointSet {
  constructor() {
    this.parent = new Map();
  }

  add(element) {
    this.parent.set(element, element);
  }

  find(element) {
    if (!this.parent.has(element)) {
      return null;
    }
    if (this.parent.get(element) === element) {
      return element;
    }
    return this.find(this.parent.get(element));
  }

  union(element1, element2) {
    let root1 = this.find(element1);
    let root2 = this.find(element2);
    if (root1 !== root2) {
      this.parent.set(root1, root2);
    }
  }
}

let set = new DisjointSet();
set.add(1);
set.add(2);
set.add(3);
set.add(4);
console.log(set.find(1)); // 1
console.log(set.find(2)); // 2
console.log(set.find(3)); // 3
console.log(set.find(4)); // 4
set.union(1, 2);
set.union(3, 4);
console.log(set.find(1)); // 2
console.log(set.find(2)); // 2
console.log(set.find(3)); // 4
console.log(set.find(4)); // 4
```

In this example, the `DisjointSet` class has the following methods:

 - `add(element)`: This method adds an element to the disjoint set.
 - `find(element)`: This method finds the root element of the subset that the given element belongs to.
 - `union(element1, element2)`: This method unites the subsets that the two given elements belong to into a single subset.
