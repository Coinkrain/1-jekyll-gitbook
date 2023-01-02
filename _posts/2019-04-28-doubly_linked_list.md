---
title: Doubly Linked List
author: Subhahu Jain
date: 2019-04-28
category: Data-Structure
layout: post
---

A doubly linked list is a linear data structure in which each element is stored in a node, and each node has pointers to the previous and next nodes in the list. Here is an example of a doubly linked list class in JavaScript:

```js
class DoublyLinkedList {
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
      newNode.prev = this.tail;
      this.tail = newNode;
    }
  }

  removeFromHead() {
    if (!this.head) return null;
    const val = this.head.value;
    this.head = this.head.next;
    if (this.head) this.head.prev = null;
    else this.tail = null;
    return val;
  }

  removeFromTail() {
    if (!this.tail) return null;
    const val = this.tail.value;
    this.tail = this.tail.prev;
    if (this.tail) this.tail.next = null;
    else this.head = null;
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
    this.prev = null;
    this.next = null;
  }
}
```

To use this doubly linked list class, you can create a new instance and add elements to the tail of the list using the addToTail method:

```js
const list = new DoublyLinkedList();
list.addToTail(1);
list.addToTail(2);
list.addToTail(3);
```

You can remove elements from the head or tail of the list using the removeFromHead and removeFromTail methods:

```js
const removedHead = list.removeFromHead();  // removedHead = 1
const removedTail = list.removeFromTail();  // removedTail = 3
```

You can check if the list contains a specific value using the contains method:

```js
const containsTwo = list.contains(2);  // containsTwo = true
const containsFour = list.contains(4);  // containsFour = false
```


[1]: https://pages.github.com
[2]: https://github.com/sighingnow/jekyll-gitbook/fork
[3]: https://pages.github.com/themes
[4]: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll
[5]: https://github.com/sighingnow/jekyll-gitbook/fork
[6]: https://github.com/sighingnow/jekyll-gitbook/blob/master/_config.yml
