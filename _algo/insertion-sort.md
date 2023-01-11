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



A recursive implementation of insertion sort involves breaking the problem down into smaller subproblems. Each recursive call processes one element of the array, and the function is called recursively on the remaining portion of the array. Once the recursive calls have returned, the element is then inserted into the correct position in the sorted portion of the array.

Here is an example of how you might implement a recursive version of insertion sort in JavaScript:

```js
function insertionSortRecursive(arr, n) {
    if (n <= 1) {
        return;
    }
    insertionSortRecursive(arr, n - 1);
    let key = arr[n - 1];
    let j = n - 2;
    while (j >= 0 && arr[j] > key) {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = key;
}
```

The time complexity of the recursive insertion sort is the same as the iterative one which is O(n^2) in the worst case and best case, but when it comes to the space complexity, the recursive version have a O(n) space complexity, due to the call stack consumed by the recursive function calls.

Insertion sort is one of the simplest sorting algorithm, it is less efficient than other sorting algorithms such as quicksort, mergesort, and heapsort when sorting large arrays.


### Questions Based on Insertion Sort
