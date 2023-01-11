---
title: Binary Search
author: Tao He
date: 2023-01-01
category: Algorithm
layout: post
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

> ##### TIP
>
> Note that this function assumes that the input array is already sorted in ascending order. If the array is not sorted, you will need to sort it first  
> before performing the binary search.
{: .block-tip }


Binary search can be implemented recursively by breaking the problem down into smaller subproblems. The basic idea is to find the middle element of the array, and compare it to the target element. If the middle element is equal to the target element, we have found our answer. If the middle element is less than the target element, we know that the target element must be in the right half of the array, so we recursively call the binary search function on the right half. If the middle element is greater than the target element, we know that the target element must be in the left half of the array, so we recursively call the binary search function on the left half. This process continues until the target element is found, or the subarray being searched is empty (indicating that the element is not present in the array).

Here is an example of how you might implement a recursive binary search function in JavaScript:

```js
function binarySearchRecursive(arr, target, left, right) {
    if (left > right) return -1; // Element not found

    let middle = Math.floor((left + right) / 2);

    if (arr[middle] === target) {
        return middle;
    } else if (arr[middle] < target) {
        return binarySearchRecursive(arr, target, middle + 1, right);
    } else {
        return binarySearchRecursive(arr, target, left, middle - 1);
    }
}
```

It is important to notice that this recursive approach might come with a big drawback which is the stackoverflow error. If the array is very large, the amount of recursion required to find the element may cause the function to exceed the maximum call stack size and crash the program.

A common way to avoid this is by using a while loop instead of recursion to perform the binary search. It will be more efficient and not have the risk of stack overflow.


### Questions Based on Binary Search
