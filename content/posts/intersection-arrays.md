---
author: "Kirti Bhardwaj"
date: 2019-05-11
linktitle: intersection-arrays
prev: /posts/median-sorted-array
title: Arrays in JS- Intersection Of Two Arrays
weight: 10
draft: false
---

### Problem Statement

Given two arrays, write a function to compute their intersection.The result can be in any order.
**Each element in the result should be unique**

Here is the LeetCode link to the problem: [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

Runtime for this solution is 52 ms.


### Test Cases:

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]

Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]

### Code

    /**
    * @param {number[]} nums1
    * @param {number[]} nums2
    * @return {number[]}
    */
    var intersection = function(nums1, nums2) {
        
        let arr = [];
        
        let arr1 = [...new Set(nums1)];
        let arr2 = [...new Set(nums2)];
        
        const len1 = arr1.length;
        const len2 = arr2.length;
        
        if(len1 > len2){
            arr1.map((el) => {
                if(arr2.includes(el)){
                    arr.push(el)
                }
            })
        }else{
            arr2.map((el) => {
                if(arr1.includes(el)){
                    arr.push(el)
                }
            })
        }
        
        return arr;
    };


### Other Problems

Now let's tweak the other problem a bit. Instead of **Each element in the result should be unique** we now add a condition where **Each element in the result should appear as many times as it shows in both arrays.**

Here is the LeetCode link to the above problem: [350. Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

Let's look at some test cases for this:

### Test Cases:

Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]

Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]


### Solution1

    /**
    * @param {number[]} nums1
    * @param {number[]} nums2
    * @return {number[]}
    */
    let sortFunction = (a,b) => a-b;
    var intersect = function(nums1, nums2) {
        let a1 = nums1.sort(sortFunction);
        let a2 = nums2.sort(sortFunction);
        let intersection = [];
        
        while(a1.length && a2.length){
            if(a1[0] === a2[0]){
                intersection.push(a1.shift());
                a2.shift();
            } 
            else if(a1[0] > a2[0]){
                a2.shift();
            }else{
                a1.shift();
            }
        }
        
        return intersection;
    };

### Solution2

    var intersect = function(nums1, nums2) {
        
        if(nums1.length === 0) return nums1;
        if(nums2.length === 0) return nums2;
        
        
        if(nums1.length > nums2.length){
            return intersect(nums2,nums1);
        }
        
        const obj = nums1.reduce((acc, el) => {
            return acc.set(el, acc.get(el) && (acc.get(el) + 1) || 1);
        }, new Map());

        return nums2.filter(i => {
            return obj.get(i) ? obj.set(i, obj.get(i) - 1) || true : false;
        });
    };