---
title: Knuth-Morris-Pratt Algorithm
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Knuth-Morris-Pratt (KMP) is an algorithm for finding patterns in strings that is faster than the naive algorithm. It works by using information about the pattern to avoid unnecessary comparisons and to skip over parts of the text that cannot match the pattern.

Here is an example of how to implement Knuth-Morris-Pratt in JavaScript:

```js
function kmp(text, pattern) {
  let n = text.length;
  let m = pattern.length;
  let fail = computeFail(pattern);
  let i = 0;
  let j = 0;
  while (i < n) {
    if (text[i] === pattern[j]) {
      if (j === m - 1) {
        return i - m + 1;
      }
      i++;
      j++;
    } else if (j > 0) {
      j = fail[j - 1];
    } else {
      i++;
    }
  }
  return -1;
}

function computeFail(pattern) {
  let m = pattern.length;
  let fail = new Array(m).fill(0);
  let i = 1;
  let j = 0;
  while (i < m) {
    if (pattern[i] === pattern[j]) {
      fail[i] = j + 1;
      i++;
      j++;
    } else if (j > 0) {
      j = fail[j - 1];
    } else {
      i++;
    }
  }
  return fail;
}
```

In this example, the `kmp` function takes a text string and a pattern string as arguments and returns the index of the first occurrence of the pattern in the text, or -1 if the pattern is not found. The `computeFail` function is a helper function that is used to compute the "fail" array, which stores the length of the longest prefix of the pattern that is also a suffix of the pattern up to a given index.