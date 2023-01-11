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


Here is an example of how you might implement a recursive version of selection sort in JavaScript:

```js
function selectionSortRecursive(arr, n) {
    // Base case: if the array has only one element, it is already sorted
    if (n <= 1) return arr;

    // Find the index of the minimum element in the unsorted part of the array
    let minIndex = 0;
    for (let i = 1; i < n; i++) {
        if (arr[i] < arr[minIndex]) {
            minIndex = i;
        }
    }

    // Swap the minimum element with the first element of the unsorted part
    [arr[minIndex], arr[n-1]] = [arr[n-1], arr[minIndex]];

    // Recursively sort the remaining unsorted part of the array
    return selectionSortRecursive(arr, n - 1);
}
```

It's important to notice that the time complexity of recursive selection sort is O(n^2) as well like the iterative one, and this is because the nested loop. Additionally, the space complexity will be O(n) because the recursion call stack may consume O(n) space.

Recursive version of the selection sort, is not as efficient as the iterative one, and it is rare to use it in practice, as it can be more complex to understand and also have a high time and space complexity. So, it's better to use an iterative selection sort.


### Questions Based on Selection Sort