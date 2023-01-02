---
title: Binary Search
author: Tao He
date: 2023-01-01
category: Algorithm
layout: post
cover: https://sighingnow.github.io/jekyll-gitbook/assets/dinosaur.gif
---


Binary search is an algorithm for finding the position of an element in a sorted array. It works by repeatedly dividing the search interval in half and comparing the element being searched for with the middle element of the interval. If the element being searched for is smaller than the middle element, then the search continues in the lower half of the interval. If the element being searched for is larger than the middle element, then the search continues in the upper half of the interval.

Here is an example of a function that performs a binary search in JavaScript:

```js
function binarySearch(array, target) {
  let left = 0;
  let right = array.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (array[mid] === target) return mid;
    if (array[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
}
```
To use this function, you can pass in an array and the element you want to search for as arguments:

```js
const array = [1, 2, 3, 4, 5];
const target = 3;
const index = binarySearch(array, target);  // index = 2
```

This function returns the index of the target element if it is found in the array, or -1 if it is not found.

> Note that this function assumes that the input array is already sorted in ascending order. If the array is not sorted, you will need to sort it first  
> before performing the binary search.
