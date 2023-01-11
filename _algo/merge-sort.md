---
title: Merge Sort
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


Merge sort is a comparison-based sorting algorithm that works by dividing an array into two halves, sorting each half, and then merging the sorted halves back together. It has a time complexity of O(n log n), which makes it more efficient than bubble sort and insertion sort.

Here is an example of how to implement merge sort in JavaScript:

```js
function mergeSort(array) {
  if (array.length <= 1) {
    return array;
  }

  let middle = Math.floor(array.length / 2);
  let left = array.slice(0, middle);
  let right = array.slice(middle);

  left = mergeSort(left);
  right = mergeSort(right);

  return merge(left, right);
}

function merge(left, right) {
  let result = [];
  while (left.length > 0 && right.length > 0) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }
  return result.concat(left).concat(right);
}
```

Here are the methods of the merge sort algorithm that are implemented in above code:

 - `mergeSort(array)`: This is the main function that performs the merge sort. It takes an array as an argument and returns a new array that is sorted in ascending order.

 - `merge(left, right)`: This is a helper function that is used to merge two sorted arrays into a single sorted array. It takes two arguments: `left` and `right`, which are the two arrays to be merged. The function returns a new array that is the result of merging the two input arrays.