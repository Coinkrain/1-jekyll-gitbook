---
title: Huffman Coding
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Huffman coding is an algorithm for constructing a prefix code that can be used for data compression. It works by assigning variable-length codes to the characters of a message such that the most frequent characters have the shortest codes.

Here is an example of how to implement Huffman coding in JavaScript:

```js
function huffmanCoding(message) {
  let frequency = {};
  for (let i = 0; i < message.length; i++) {
    let character = message[i];
    if (frequency[character]) {
      frequency[character]++;
    } else {
      frequency[character] = 1;
    }
  }

  let priorityQueue = new PriorityQueue((a, b) => a.frequency - b.frequency);
  for (let character in frequency) {
    priorityQueue.enqueue(new Node(character, frequency[character]));
  }

  while (priorityQueue.size() > 1) {
    let left = priorityQueue.dequeue();
    let right = priorityQueue.dequeue();
    let sum = left.frequency + right.frequency;
    priorityQueue.enqueue(new Node(null, sum, left, right));
  }

  let root = priorityQueue.dequeue();
  let codes = {};
  generateCodes(root, "", codes);
  return codes;
}

function generateCodes(node, code, codes) {
  if (node.character) {
    codes[node.character] = code;
  } else {
    generateCodes(node.left, code + "0", codes);
    generateCodes(node.right, code + "1", codes);
  }
}

class Node {
  constructor(character, frequency, left, right) {
    this.character = character;
    this.frequency = frequency;
    this.left = left;
    this.right = right;
  }
}
```

In this example, the `huffmanCoding` function takes a message as an argument and returns an object with the Huffman codes for each character in the message. The function works by first calculating the frequencies of each character in the message, creating a priority queue of nodes representing the characters, and then building the Huffman tree using the priority queue. The `generateCodes` function is a helper function that is used to generate the Huffman codes by traversing the Huffman tree in a depth-first manner.

