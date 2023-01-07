---
title: Merge vs Quick Sort
author: Subhahu Jain
date: 2023-01-01
category: Algorithm
layout: post
---

Here is a comparison of merge sort and quick sort in table form:


| Property | Merge Sort | Quick Sort |
| --- | --- | --- |
| Time complexity (worst) | O(n * logn) | O(n^2) |
| Time complexity (average) | O(n * logn) | O(n * logn) |
| Space complexity | O(n) | O(logn) |
| Stable | Yes | No |
| In-place | No | Yes |
| Divide-and-conquer | Yes | Yes |
| Recursive | Yes | Yes |
| Comparison-based | Yes | Yes |

-   Time complexity: The time complexity of an algorithm is a measure of the amount of time it takes to run as a function of the size of the input. In the case of sorting algorithms, the time complexity is usually expressed as a function of the number of elements in the list being sorted. Both merge sort and quick sort have a time complexity of O(n * logn) in the average and best cases, meaning the time taken to sort the list increases logarithmically with the number of elements. However, quick sort has a worst-case time complexity of O(n^2), meaning it can take quadratic time to sort a list if the pivot is poorly chosen.

-   Space complexity: The space complexity of an algorithm is a measure of the amount of memory it uses as a function of the size of the input. In the case of sorting algorithms, the space complexity is usually expressed as a function of the number of elements in the list being sorted. Merge sort has a space complexity of O(n), meaning it requires additional space to store the temporary sublists during the sorting process. Quick sort has a space complexity of O(logn), meaning it only requires a constant amount of additional space to store the recursion stack.

-   Stable: A stable sorting algorithm is one that preserves the relative order of equal elements during the sorting process. This means that if two elements are equal, their order in the sorted list will be the same as their order in the original list. Merge sort is a stable sorting algorithm, but quick sort is not.

-   In-place: An in-place sorting algorithm is one that sorts the list using only a constant amount of additional space, without creating any additional arrays or lists. Quick sort is an in-place sorting algorithm, but merge sort is not.

-   Divide-and-conquer: Both merge sort and quick sort use a divide-and-conquer approach to sorting, meaning they divide the list into smaller pieces, sort them independently, and then combine them back together.

-   Recursive: Both merge sort and quick sort are recursive algorithms, meaning they use recursion to divide the list into smaller pieces and combine the sorted pieces back together.

-   Comparison-based: Both merge sort and quick sort are comparison-based sorting algorithms, meaning they sort the list by comparing the elements to each other.