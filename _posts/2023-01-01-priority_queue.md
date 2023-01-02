---
title: Priority Queue
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A priority queue is a data structure that allows you to store a set of items with associated priorities, and retrieve the items in order of their priority. It is often implemented as a heap, with the highest priority item being at the top of the heap.

In JavaScript, you can implement a priority queue by creating a class or a constructor function that represents the queue. The queue can be implemented as an array, with the highest priority item at the front of the array. You can use the built-in Array.sort method to sort the array based on the priorities of the items, and use the push and shift methods to add and remove items from the queue.

Here is an example of a simple priority queue class in JavaScript:

```js
class PriorityQueue {
  constructor() {
    this.items = [];
  }

  enqueue(item, priority) {
    this.items.push({item: item, priority: priority});
    this.items.sort((a, b) => a.priority - b.priority);
  }

  dequeue() {
    return this.items.shift().item;
  }
}

let queue = new PriorityQueue();
queue.enqueue("apple", 1);
queue.enqueue("banana", 2);
queue.enqueue("cherry", 3);
console.log(queue.dequeue());  // Output: "cherry"
console.log(queue.dequeue());  // Output: "banana"
console.log(queue.dequeue());  // Output: "apple"
```
