---
title: Array
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


Arrays in JavaScript are ordered collections of values that can be of any data type, including numbers, strings, objects, and even other arrays. You can create an array in JavaScript by using the `Array` constructor or by using the array literal syntax, which is an array of values enclosed in square brackets.

Here are some examples of creating arrays in JavaScript:

```js
// Using the Array constructor
let arr1 = new Array();
let arr2 = new Array(1, 2, 3);
let arr3 = new Array(5); // Creates an array of length 5

// Using the array literal syntax
let arr4 = [];
let arr5 = [1, 2, 3];
let arr6 = [1, "two", { three: 3 }];
You can access and modify the elements of an array using their index, which is the position of the element in the array. Arrays are zero-indexed, which means that the first element has an index of 0, the second element has an index of 1, and so on.

Here are some examples of accessing and modifying the elements of an array in JavaScript:

Copy code
let arr = [1, 2, 3];

// Accessing an element
let first = arr[0]; // 1
let second = arr[1]; // 2

// Modifying an element
arr[0] = 10; // [10, 2, 3]
arr[2] = "three"; // [10, 2, "three"]
```

You can also use various array methods to manipulate the elements of an array, such as `push` to add an element to the end of the array, `pop` to remove the last element of the array, `shift` to remove the first element of the array, and `unshift` to add an element to the beginning of the array.