
---
author: "Kirti Bhardwaj"
date: 2023-11-24
linktitle: array-easy
prev: /posts/median-sorted-array
title: Arrays in JS- Some Easy Problems
weight: 10
draft: true
---

### 1 Problem Statement [Move Zeroes]

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:
    Input: [0,1,0,3,12]
    Output: [1,3,12,0,0]
Note:
1) You must do this in-place without making a copy of the array.
2) Minimize the total number of operations.


### Solution
    /**
    * @param {number[]} nums
    * @return {void} Do not return anything, modify nums in-place instead.
    */
    var moveZeroes = function(nums) {
        let len = nums.length;
        for(let i = 0; i<= nums.length;i++){
            if(nums[i] === 0){
                nums.push(nums.splice(i,1));
                i -=1;
            }
        }
    };