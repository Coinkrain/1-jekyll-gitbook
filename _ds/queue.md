---
title: Queue
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A queue is a data structure that follows the first-in, first-out (FIFO) principle, allowing you to enqueue (add) elements to the back of the queue and dequeue (remove) elements from the front of the queue.

In JavaScript, you can implement a queue by creating a class or a constructor function that represents the queue. The queue can be implemented as an array, with the front of the queue at the beginning of the array and the back of the queue at the end of the array. You can use the built-in Array.unshift and Array.push methods to add elements to the queue, and the Array.shift method to remove elements from the front of the queue.

Here is an example of a simple queue class in JavaScript:

```js
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(item) {
    this.items.push(item);
  }

  dequeue() {
    return this.items.shift();
  }

  peek() {
    return this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}

let queue = new Queue();
queue.enqueue("apple");
queue.enqueue("banana");
queue.enqueue("cherry");
console.log(queue.size()); // 3
console.log(queue.peek()); // "apple"
console.log(queue.dequeue()); // "apple"
console.log(queue.size()); // 2
```

 The queue class has the following methods:

 - `enqueue(item)`: This method adds an element to the back of the queue.
 - `dequeue()`: This method removes an element from the front of the queue and returns it.
 - `peek()`: This method returns the element at the front of the queue, without removing it.
 - `isEmpty()`: This method returns a boolean value indicating whether the queue is empty or not.
 - `size()`: This method returns the number of elements in the queue.


