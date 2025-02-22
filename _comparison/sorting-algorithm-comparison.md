---
title: Sorting Algorithm Comparison
author: Subhahu Jain
date: 2023-01-01
category: Algorithm
layout: post
---



Here is a list of comparison between different sorting algorithms:

| Algorithm | Time complexity (worst) | Time complexity (average) | Space complexity | Stable | In-place |
| --- | --- | --- | --- | --- | --- |
| Bubble sort | O(n^2) | O(n^2) | O(1) | Yes | Yes |
| Insertion sort | O(n^2) | O(n^2) | O(1) | Yes | Yes |
| Selection sort | O(n^2) | O(n^2) | O(1) | No | Yes |
| Shell sort | O(n^2) | O(n^1.5) | O(1) | No | Yes |
| Merge sort | O(n * logn) | O(n * logn) | O(n) | Yes | No |
| Quick sort | O(n^2) | O(n * logn) | O(logn) | No | Yes |
| Heap sort | O(n * logn) | O(n * logn) | O(1) | No | Yes |
| Tim sort | O(n * logn) | O(n * logn) | O(n) | Yes | No |
| Radix sort | O(n * k) | O(n * k) | O(n + k) | Yes | Yes |

-   Time complexity: The time complexity of an algorithm is a measure of the amount of time it takes to run as a function of the size of the input. In the case of sorting algorithms, the time complexity is usually expressed as a function of the number of elements in the list being sorted.

-   Space complexity: The space complexity of an algorithm is a measure of the amount of memory it uses as a function of the size of the input. In the case of sorting algorithms, the space complexity is usually expressed as a function of the number of elements in the list being sorted.

-   Stable: A stable sorting algorithm is one that preserve the relative order of equal elements during the sorting process. This means that if two elements are equal, their order in the sorted list will be the same as their order in the original list.

-   In-place: An in-place sorting algorithm is one that sorts the list using only a constant amount of additional space, without creating any additional arrays or lists.