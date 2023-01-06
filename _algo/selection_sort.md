---
title: Selection Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Selection sort is a simple sorting algorithm that works by repeatedly finding the minimum element from the unsorted portion of the array and adding it to the sorted portion of the array. It has a time complexity of O(n^2), which makes it less efficient than other sorting algorithms such as merge sort and quick sort.

Here is an example of how to implement selection sort in JavaScript:

```js
function selectionSort(array) {
  for (let i = 0; i < array.length; i++) {
    let minIndex = i;
    for (let j = i + 1; j < array.length; j++) {
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }
    }
    [array[i], array[minIndex]] = [array[minIndex], array[i]];
  }
  return array;
}
```

In this example, the selectionSort function takes an array as an argument and returns a new array that is sorted in ascending order. The function works by iterating through the array and selecting the minimum element from the unsorted portion of the array at each step. It then swaps the minimum element with the first element of the unsorted portion of the array, effectively adding the minimum element to the sorted portion of the array.

