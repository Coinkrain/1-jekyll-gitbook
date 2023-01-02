---
title: Deque
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---

A deque (short for "double-ended queue") is a data structure that allows you to store a set of items and perform operations on both ends of the queue. It is similar to a queue or a stack, but allows you to add and remove items from either the front or the back of the queue.

In JavaScript, you can implement a deque by creating a class or a constructor function that represents the deque. The deque can be implemented as an array, with the front of the deque at the beginning of the array and the back of the deque at the end of the array. You can use the built-in Array.unshift and Array.push methods to add items to the deque, and the Array.shift and Array.pop methods to remove items from the deque.

Here is an example of a simple deque class in JavaScript:

```js
class Deque {
  constructor() {
    this.items = [];
  }

  addFront(item) {
    this.items.unshift(item);
  }

  addBack(item) {
    this.items.push(item);
  }

  removeFront() {
    return this.items.shift();
  }

  removeBack() {
    return this.items.pop();
  }

  peekFront() {
    return this.items[0];
  }

  peekBack() {
    return this.items[this.items.length - 1];
  }
}
```


