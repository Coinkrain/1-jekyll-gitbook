---
title: Boyer's Moore
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Boyer-Moore is a string matching algorithm that is designed to be efficient in terms of time complexity. It works by using a preprocessing step to skip over certain characters in the text, which allows it to avoid unnecessary comparisons and find the pattern faster.

Here is an example of how to implement the Boyer-Moore algorithm in JavaScript:

```js
function boyerMoore(text, pattern) {
  let skipTable = preprocess(pattern);
  let i = pattern.length - 1;
  while (i < text.length) {
    let j = pattern.length - 1;
    while (j >= 0 && text[i] === pattern[j]) {
      i--;
      j--;
    }
    if (j === -1) {
      return i + 1; // pattern found
    }
    i += skipTable[text.charCodeAt(i)];
  }
  return -1; // pattern not found
}

function preprocess(pattern) {
  let skipTable = new Uint32Array(128);
  for (let i = 0; i < skipTable.length; i++) {
    skipTable[i] = pattern.length;
  }
  for (let i = 0; i < pattern.length - 1; i++) {
    skipTable[pattern.charCodeAt(i)] = pattern.length - 1 - i;
  }
  return skipTable;
}
```

In this example, the `boyerMoore` function takes a text string and a pattern as arguments and returns the index of the first occurrence of the pattern in the text, or -1 if the pattern is not found. The `preprocess` function is a helper function that creates a skip table based on the characters in the pattern. The skip table is used to skip over certain characters in the text during the search, which allows the algorithm to avoid unnecessary comparisons and find the pattern faster.