---
title: Stack
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A stack is a Last In, First Out (LIFO) data structure. You can use an array to implement a stack in JavaScript. Here is an example of a stack class that uses an array to store the stack elements:

```js
class Stack {
  constructor() {
    this.items = [];
  }

  push(item) {
    this.items.push(item);
  }

  pop() {
    return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}
```

To use this stack class, you can create a new instance and push elements onto the stack using the push method:

```js
const stack = new Stack();
stack.push(1);
stack.push(2);
stack.push(3);
```

You can remove elements from the top of the stack using the pop method:

```js
const popped = stack.pop();  // popped = 3
```

You can retrieve the element at the top of the stack without removing it using the peek method:

```js
const peeked = stack.peek();  // peeked = 2
```

You can check if the stack is empty using the isEmpty method:

```js
const empty = stack.isEmpty();  // empty = false
```

You can get the size of the stack using the size method:

```js
const size = stack.size();  // size = 2
```

