---
title: Bubble Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Bubble sort is an algorithm for sorting elements in an array. It works by repeatedly iterating through the array, comparing adjacent elements and swapping them if they are in the wrong order. The process is repeated until the array is sorted.

Here is an example of a function that performs a bubble sort in JavaScript:

```js
function bubbleSort(array) {
  let swapped;
  do {
    swapped = false;
    for (let i = 0; i < array.length - 1; i++) {
      if (array[i] > array[i + 1]) {
        [array[i], array[i + 1]] = [array[i + 1], array[i]];
        swapped = true;
      }
    }
  } while (swapped);
  return array;
}
```

To use this function, you can pass in the array that you want to sort as an argument:

```js
const array = [5, 2, 1, 3, 4];
const sortedArray = bubbleSort(array);  // sortedArray = [1, 2, 3, 4, 5]
```

This function returns a new array that is sorted in ascending order.

Note that the time complexity of bubble sort is O(n^2), so it may not be the most efficient sorting algorithm for large arrays. There are many other sorting algorithms that have a better time complexity, such as quicksort or mergesort.