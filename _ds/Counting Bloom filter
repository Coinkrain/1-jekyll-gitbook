---
title: Counting Bloom Filter
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A counting Bloom filter is a variant of the Bloom filter data structure that allows for the insertion, deletion, and membership testing of elements, while providing a probabilistic guarantee of the number of elements stored in the filter. It works by using multiple hash functions to map elements to a fixed-size bit array, and storing the count of how many times an element has been inserted into each position in the array.

Here is an example of a simple counting Bloom filter class in JavaScript:

```js
class CountingBloomFilter {
  constructor(size, hashCount) {
    this.size = size;
    this.hashCount = hashCount;
    this.counts = new Array(size).fill(0);
  }

  insert(element) {
    for (let i = 0; i < this.hashCount; i++) {
      let index = this._hash(element, i);
      this.counts[index]++;
    }
  }

  delete(element) {
    for (let i = 0; i < this.hashCount; i++) {
      let index = this._hash(element, i);
      this.counts[index]--;
    }
  }

  test(element) {
    for (let i = 0; i < this.hashCount; i++) {
      let index = this._hash(element, i);
      if (this.counts[index] <= 0) {
        return false;
      }
    }
    return true;
  }

  _hash(element, seed) {
    let hash = 0;
    for (let i = 0; i < element.length; i++) {
      hash = (hash + element.charCodeAt(i) + seed) % this.size;
    }
    return hash;
  }
}
```

In this example, the `CountingBloomFilter` class has a constructor that initializes a new counting Bloom filter with a given size and number of hash functions, and four methods: `insert`, `delete`, `test`, and `_hash`. The `insert` and `delete` methods add or remove an element from the filter, respectively, by incrementing or decrementing the count at each position in the array that the element maps to. The `test` method returns `true` if an element is probably in the filter, or `false` otherwise, based on the counts at the positions in the array that the element maps to. The `_hash` method is a helper function that maps an element to a position in the array using a given seed value for the hash function.

