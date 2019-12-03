---
author: "Kirti Bhardwaj"
date: 2019-11-24
linktitle: invert-binary-tree
prev: /posts/median-sorted-array
title: Invert A Binary Tree
weight: 10
draft: false
---


### Problem Statement
Invert a binary tree. Here is the leetCode link [Invert A Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

**Example:**

    Input:

         4
       /   \
      2     7
     / \   / \
    1   3 6   9
    
    Output:

         4
       /   \
      7     2
     / \   / \
    9   6 3   1

### Solution 

This is not a difficult problem to solve. We write a recursive invertTree function, let's look at the code.

    /**
    * Definition for a binary tree node.
    * function TreeNode(val) {
    *     this.val = val;
    *     this.left = this.right = null;
    * }
    */
    /**
    * @param {TreeNode} root
    * @return {TreeNode}
    */
    var invertTree = function(root) {
        if(!root) return root;
        let right = invertTree(root.right);
        let left = invertTree(root.left);
        
        root.left = right || null;
        root.right = left || null;
            
        return root;
    };