---
title: Segment tree
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---


A segment tree is a data structure that allows you to efficiently store and query intervals or segments. It is a tree-based data structure that can be used to perform range queries (such as finding the minimum or maximum value in a range) in O(log n) time, and range updates (such as adding or multiplying all values in a range) in O(log n) time.

In JavaScript, you can implement a segment tree by creating a class or a constructor function that represents a node in the tree. Each node in the segment tree represents a range of values, and has left and right children that represent the ranges of values that are split off from the parent range. The root node represents the entire range of values, and the leaf nodes represent the individual values in the range.

Here is an example of a simple segment tree class in JavaScript:

The SegmentTreeNode class is a helper class that represents a node in the segment tree. Each node in the segment tree represents a range of values, and has left and right children that represent the ranges of values that are split off from the parent range.

Here is the full implementation of the SegmentTreeNode class:

```js
class SegmentTreeNode {
  constructor(start, end) {
    this.start = start;
    this.end = end;
    this.min = null;
    this.left = null;
    this.right = null;
  }
}
```
The SegmentTreeNode class has the following properties:

 - `start`: This is the starting index of the range of values represented by the node.
 - `end`: This is the ending index of the range of values represented by the node.
 - `min`: This is the minimum value in the range of values represented by the node.
 - `left`: This is a reference to the left child of the node, which represents the range of values that is split off from the parent range.
 - `right`: This is a reference to the right child of the node, which represents the range of values that is split off from the parent range.
I hope this helps! Let me know if you have any questions or need more information.



The SegmentTree class is a data structure that represents a segment tree. A segment tree is a tree-based data structure that can be used to perform range queries (such as finding the minimum or maximum value in a range) in O(log n) time, and range updates (such as adding or multiplying all values in a range) in O(log n) time.

Here is the full implementation of the SegmentTree class:

```js
class SegmentTree {
  constructor(nums) {
    this.root = this._buildTree(nums, 0, nums.length - 1);
  }

  _buildTree(nums, start, end) {
    if (start > end) return null;

    let root = new SegmentTreeNode(start, end);
    if (start === end) {
      root.min = nums[start];
    } else {
      let mid = start + Math.floor((end - start) / 2);
      root.left = this._buildTree(nums, start, mid);
      root.right = this._buildTree(nums, mid + 1, end);
      root.min = Math.min(root.left.min, root.right.min);
    }
    return root;
  }

  update(i, val) {
    this._update(this.root, i, val);
  }

_update(root, i, val) {
  if (!root) return;

  if (root.start === root.end) {
    root.min = val;
    return;
  }

  let mid = root.start + Math.floor((root.end - root.start) / 2);
  if (i <= mid) {
    this._update(root.left, i, val);
  } else {
    this._update(root.right, i, val);
  }
  root.min = Math.min(root.left.min, root.right.min);
}

query(start, end) {
  return this._query(this.root, start, end);
}


_query(root, start, end) {
  if (!root || root.start > end || root.end < start) return Number.MAX_SAFE_INTEGER;
  if (root.start >= start && root.end <= end) return root.min;

  let mid = root.start + Math.floor((root.end - root.start) / 2);
  let left = this._query(root.left, start, end);
  let right = this._query(root.right, start, end);
  return Math.min(left, right);
}

}
        
```

The SegmentTree class is a data structure that represents a segment tree. A segment tree is a tree-based data structure that can be used to perform range queries (such as finding the minimum or maximum value in a range) in O(log n) time, and range updates (such as adding or multiplying all values in a range) in O(log n) time.

Here is a list of the methods that are implemented in the SegmentTree class:

 - `constructor(nums)`: This is the constructor function for the SegmentTree class. It takes an array of numbers as input, and uses the _buildTree method to construct the segment tree from the array.

 - `_buildTree(nums, start, end)`: This is a helper method that builds the segment tree from the given array of numbers. It recursively creates SegmentTreeNode objects for each range of values in the array, and sets the min property of each node to the minimum value in the range.

 - `update(i, val)`: This method updates the value at the specified index in the array. It calls the _update method to update the value in the segment tree and update the min values of the nodes in the tree.

 - `_update(root, i, val)`: This is a helper method that updates the value in the segment tree at the specified index. It recursively traverses the tree until it finds the leaf node that represents the specified index, and updates the value in that node.

 - `query(start, end)`: This method returns the minimum value in the specified range of the array. It calls the _query method to search for the minimum value in the segment tree.

 - `_query(root, start, end)`: This is a helper method that searches for the minimum value in the specified range in the segment tree. It recursively traverses the tree and returns the minimum value in the range based on the values in the nodes of the tree.

