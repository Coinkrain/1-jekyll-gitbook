---
title: Linked List
author: Subhahu Jain
date: 2019-04-27
category: Data-Structure
layout: post
---

A linked list is a linear data structure in which elements are stored in nodes, and each node points to the next node in the list. Here is an example of a linked list class in JavaScript:

```javascript
class LinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  addToTail(value) {
    const newNode = new Node(value);
    if (!this.head) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
  }

  removeFromHead() {
    if (!this.head) return null;
    const val = this.head.value;
    this.head = this.head.next;
    if (!this.head) this.tail = null;
    return val;
  }

  contains(value) {
    let currentNode = this.head;
    while (currentNode) {
      if (currentNode.value === value) return true;
      currentNode = currentNode.next;
    }
    return false;
  }
}

class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}
```

To use this linked list class, you can create a new instance and add elements to the tail of the list using the addToTail method:

```js
const list = new LinkedList();
list.addToTail(1);
list.addToTail(2);
list.addToTail(3);
```

You can remove elements from the head of the list using the removeFromHead method:

```js
const removed = list.removeFromHead();  // removed = 1
```

You can check if the list contains a specific value using the contains method:

```js
const containsTwo = list.contains(2);  // containsTwo = true
const containsFour = list.contains(4);  // containsFour = false
```

[1]: https://pages.github.com
