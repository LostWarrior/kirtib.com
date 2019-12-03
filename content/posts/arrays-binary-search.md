
---
author: "Kirti Bhardwaj"
date: 2019-11-27
linktitle: array-binary-search
prev: /posts/median-sorted-array
title: Arrays in JS- Binary Search
weight: 10
draft: false
---

### Problem Statement
Given a sorted (in ascending order) integer array nums of n elements and a target value, write a function to search target in nums. If target exists, then return its index, otherwise return -1.
Here is the leetcode link to the problem [Binary Search](https://leetcode.com/problems/binary-search/)

### Examples


**Example 1:**

    Input: nums = [-1,0,3,5,9,12], target = 9
    Output: 4
    Explanation: 9 exists in nums and its index is 4

**Example 2:**

    Input: nums = [-1,0,3,5,9,12], target = 2
    Output: -1
    Explanation: 2 does not exist in nums so return -1


### Solution
Let's take a look at recursive solution first. Binary search is used to find the index of an element in a sorted array. If the element doesn’t exist, that can be determined efficiently as well. The algorithm divides the input array by half at every step. After every step, either we have found the index that we are looking for or half of the array can be discarded. Hence, solution can be calculated in O(logn) time.

Here’s how it will work.

1) At each step, check array between low and high indices. Calculate the mid index.

2) If the **value at mid === key**, return mid.

3) If the **value at mid > key**, then reduce the array size such that high becomes mid - 1.Index at low remains the same.

4) If the **value at mid < key**, then reduce the array size such that low becomes mid + 1. Index at high remains the same.

5) When low > high, key doesn’t exist. Return -1.

Iterative solution works the same way.It has the same O(logn) runtime complexity of the recursive solution but has better memory complexity O(1).

### Code

    /**
    * @param {number[]} nums
    * @param {number} target
    * @return {number}
    */
    var search = function(nums, target) {
        
        const len = nums.length;
        
        let low = 0;
        let high = len-1;
        
        while(low <= high){
            let mid = low + Math.floor((high - low)/2);
            if(nums[mid] === target){
                return mid;
            }else if(target < nums[mid]){
                high = mid-1;
            }else{
                low = mid +1;
            }
        }
        
        return -1;
    };