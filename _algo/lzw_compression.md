---
title: LZW Compression
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


LZW (Lempel-Ziv-Welch) is a lossless data compression algorithm that is based on the idea of replacing repeated patterns with a reference to a dictionary. It works by building a dictionary of patterns as it processes the input data, and replacing each pattern with its corresponding dictionary entry as it is encountered.

Here is an example of how to implement LZW compression in JavaScript:

```js
function lzwEncode(data) {
  let dictionary = {};
  let current = "";
  let result = [];
  let idx = 0;
  for (let i = 0; i < data.length; i++) {
    let char = data[i];
    let next = current + char;
    if (dictionary[next]) {
      current = next;
    } else {
      result.push(dictionary[current]);
      dictionary[next] = ++idx;
      current = char;
    }
  }
  if (current) {
    result.push(dictionary[current]);
  }
  return result;
}

function lzwDecode(data) {
  let dictionary = {};
  let current = "";
  let result = "";
  let idx = 0;
  for (let i = 0; i < data.length; i++) {
    let char = data[i];
    let next = dictionary[char];
    if (next) {
      current = next;
    } else {
      next = current + current[0];
      dictionary[char] = next;
      current = next;
    }
    result += current;
  }
  return result;
}
```

In this example, the `lzwEncode` function takes a data string as an argument and returns an array of integers representing the encoded version of the data. The `lzwDecode` function takes an array of integers as an argument and returns the decoded version of the data.