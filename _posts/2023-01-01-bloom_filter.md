---
title: Bloom filter
author: Tao He
date: 2023-01-01
category: Algorithm
layout: post
---


A Bloom filter is a probabilistic data structure that is used to test whether an element is a member of a set. It is a space-efficient data structure that allows you to test for membership in a set with a high degree of accuracy, using a fixed amount of memory.

In JavaScript, you can implement a Bloom filter by creating a class or a constructor function that represents the filter. The filter is implemented as a bit array, with each bit representing an element in the set. To add an element to the set, you can use one or more hash functions to map the element to one or more positions in the bit array, and set the corresponding bits to 1. To test for membership in the set, you can use the same hash functions to map the element to the positions in the bit array, and check if the corresponding bits are set to 1.

Here is an example of a simple Bloom filter class in JavaScript:

```js
class BloomFilter {
  constructor(size, numHashes) {
    this.size = size;
    this.numHashes = numHashes;
    this.bits = new Array(size).fill(0);
  }

  add(element) {
    for (let i = 0; i < this.numHashes; i++) {
      let hash = this._hash(element, i);
      this.bits[hash] = 1;
    }
  }

  test(element) {
    for (let i = 0; i < this.numHashes; i++) {
      let hash = this._hash(element, i);
      if (this.bits[hash] !== 1) {
        return false;
      }
    }
    return true;
  }

  _hash(element, seed) {
    let hash = 0;
    for (let i = 0; i < element.length; i++) {
      hash = (hash + element.charCodeAt(i) * seed) % this.size;
    }
    return hash;
  }
}

let filter = new BloomFilter(100, 3);
filter.add("apple");
console.log(filter.test("apple"));  // Output: true
console.log(filter.test("banana"));  // Output: false
```

In this example, the BloomFilter class represents the filter itself, and has a size (the number of bits in the bit array), a number of hash functions to use, and a bit array to store the set. The add method is used to add an element to the set, and the test method is used to test for membership in the set. The _hash method is used to map an element to a position in the bit array using a hash function.

I hope this helps! Let me know if you have any questions or need more information.


