---
title: Quick Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Quick sort is a comparison-based sorting algorithm that works by selecting a pivot element and partitioning the array around the pivot. It has a time complexity of O(n log n), which makes it more efficient than bubble sort and insertion sort.

Here is an example of how to implement quick sort in JavaScript:

```js
function quickSort(array, low, high) {
  if (low < high) {
    let pivotIndex = partition(array, low, high);
    quickSort(array, low, pivotIndex - 1);
    quickSort(array, pivotIndex + 1, high);
  }
  return array;
}

function partition(array, low, high) {
  let pivot = array[high];
  let i = low - 1;
  for (let j = low; j < high; j++) {
    if (array[j] < pivot) {
      i++;
      [array[i], array[j]] = [array[j], array[i]];
    }
  }
  [array[i + 1], array[high]] = [array[high], array[i + 1]];
  return i + 1;
}
```

In this example, the `quickSort` function takes an array as an argument and returns a new array that is sorted in ascending order. The function works by recursively partitioning the array around a pivot element until the array is fully sorted. The `partition` function is a helper function that is used to partition the array around the pivot element.