---
title: Insertion Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Insertion sort is a simple sorting algorithm that works by iterating over the elements of an array and inserting each element into its proper place in the sorted portion of the array. It has a time complexity of O(n^2), which makes it less efficient than other sorting algorithms such as merge sort and quick sort.

Here is an example of how to implement insertion sort in JavaScript:

```js
function insertionSort(array) {
  for (let i = 1; i < array.length; i++) {
    let key = array[i];
    let j = i - 1;
    while (j >= 0 && array[j] > key) {
      array[j + 1] = array[j];
      j--;
    }
    array[j + 1] = key;
  }
  return array;
}
```

In this example, the `insertionSort` function takes an array as an argument and returns a new array that is sorted in ascending order. The function works by iterating over the elements of the array and inserting each element into its proper place in the sorted portion of the array using a linear search.