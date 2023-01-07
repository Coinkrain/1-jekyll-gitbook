---
title: Splay Tree
author: Subhahu Jain
date: 2023-01-01
category: Data-Structure
layout: post
---




A splay tree is a self-balancing binary search tree that stores data in a sorted and searchable manner. It works by "splaying" the accessed elements to the root of the tree, so that frequently accessed elements are closer to the root and can be found more quickly in the future. This property allows the tree to have amortized logarithmic time complexity for the most common operations, such as search, insert, and delete.

Here is an example of a simple splay tree class in JavaScript:



```js
class SplayTree {
    constructor() {
        this.root = null;
    }

    insert(value) {
        if (this.root === null) {
            this.root = {
                value,
                left: null,
                right: null
            };
            return;
        }
        let current = this.root;
        while (true) {
            if (value < current.value) {
                if (current.left === null) {
                    current.left = {
                        value,
                        left: null,
                        right: null
                    };
                    this._splay(current.left);
                    break;
                } else {
                    current = current.left;
                }
            } else {
                if (current.right === null) {
                    current.right = {
                        value,
                        left: null,
                        right: null
                    };
                    this._splay(current.right);
                    break;
                } else {
                    current = current.right;
                }
            }
        }
    }

    search(value) {
        let current = this.root;
        while (current) {
            if (value === current.value) {
                this._splay(current);
                return true;
            } else if (value < current.value) {
                current = current.left;
            } else {
                current = current.right;
            }
        }
        return false;
    }

    delete(value) {
        if (this.root === null) {
            return;
        }
        this.search(value);
        if (this.root.value !== value) {
            return;
        }
        if (this.root.left === null) {
            this.root = this.root.right;
        } else {
            let right = this.root.right;
            this.root = this.root.left;
            this.search(value);
            this.root.right = right;
        }
    }

    _splay(node) {
        while (node !== this.root) {
            let parent = this._parent(node);
            if (parent === this.root) {
                if (parent.left === node) {
                    this._rotateRight(parent);
                } else {
                    this._rotateLeft(parent);
                }
            } else {
                let grandParent = this._parent(parent);
                if (grandParent.left === parent) {
                    if (parent.left === node) {
                        this._rotateRight(grandParent);
                        this._rotateRight(parent);
                    } else {
                        this._rotateLeft(parent);
                        this._rotateRight(grandParent);
                    }
                } else {
                    if (parent.left === node) {
                        this._rotateRight(parent);
                        this._rotateLeft(grandParent);
                    } else {
                        this._rotateLeft(grandParent);
                        this._rotateLeft(parent);
                    }
                }
            }
        }
    }



    _parent(node) {
        if (node === this.root) {
            return null;
        }
        let current = this.root;
        while (current.left !== node && current.right !== node) {
            if (current.value > node.value) {
                current = current.left;
            } else {
                current = current.right;
            }
        }
        return current;
    }

    _rotateLeft(node) {
        let right = node.right;
        node.right = right.left;
        right.left = node;
        if (node === this.root) {
            this.root = right;
        } else {
            let parent = this._parent(node);
            if (parent.left === node) {
                parent.left = right;
            } else {
                parent.right = right;
            }
        }
    }

    _rotateRight(node) {
        let left = node.left;
        node.left = left.right;
        left.right = node;
        if (node === this.root) {
            this.root = left;
        } else {
            let parent = this._parent(node);
            if (parent.left === node) {
                parent.left = left;
            } else {
                parent.right = left;
            }
        }
    }

}
```


