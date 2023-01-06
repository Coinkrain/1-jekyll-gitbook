---
title: Heap Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Heap sort is a comparison-based sorting algorithm that sorts an array by building a heap and repeatedly extracting the minimum element from the heap. It has a time complexity of O(n log n), which makes it more efficient than bubble sort and insertion sort.

Here is an example of how to implement heap sort in JavaScript:

```js
function heapSort(array) {
  let heapSize = array.length;

  // Build a max heap
  for (let i = Math.floor(heapSize / 2); i >= 0; i--) {
    heapify(array, heapSize, i);
  }

  // Extract elements from the heap one by one
  for (let i = array.length - 1; i > 0; i--) {
    // Move current root to end
    [array[0], array[i]] = [array[i], array[0]];
    // Call max heapify on the reduced heap
    heapify(array, i, 0);
  }
}

function heapify(array, heapSize, i) {
  let left = 2 * i + 1;
  let right = 2 * i + 2;
  let largest = i;

  // If the left child is larger than the root
  if (left < heapSize && array[left] > array[largest]) {
    largest = left;
  }

  // If the right child is larger than the largest so far
  if (right < heapSize && array[right] > array[largest]) {
    largest = right;
  }

  // If the largest is not the root
  if (largest !== i) {
    // Swap the root with the largest
    [array[i], array[largest]] = [array[largest], array[i]];
    // Recursively heapify the affected sub-tree
    heapify(array, heapSize, largest);
  }
}
```

Here are the methods of the heap sort algorithm that are implemented in the above code:

 - `heapSort(array)`: This is the main function that performs the heap sort. It takes an array as an argument and sorts it in-place. The function does not return anything.

 - `heapify(array, heapSize, i)`: This is a helper function that is used to build the heap and maintain the heap property. It takes three arguments: `array`, which is the array to be sorted; `heapSize`, which is the size of the heap; and i, which is the index of the root node of the sub-tree to be heapified. The function does not return anything.

