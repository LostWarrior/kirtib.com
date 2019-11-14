---
author: "Kirti Bhardwaj"
date: 2019-11-14
linktitle: integer-plus-one
prev: /posts/median-sorted-array
title: Arrays in JS- Add plus one to the integer
weight: 10
draft: false
---

### Problem Statement

Given a non-empty array of digits representing a non-negative integer, plus one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.

Here is the LeetCode link to the problem: [LeetCode: Plus One](https://leetcode.com/problems/plus-one/)


### Test Cases

Input => Output
[1,2,3]   => [1,2,4]
[4,3,2,1] => [4,3,2,2]
[1,2,9] => [1,3,0]
[9,9,9] => [1,0,0,0]
[1,9,9] => [2,0,0]

### Solution

Let's talk about the brute force solution first. If we keep track of curry and add 1 to the last element of the array, we can increment the numbers from right to left. And after looping through array if we still have a value in curry we will just append it to the beginning of the array.

Sounds, very straight forwards. However, it is not optimized. Let's take a look at the code. This is simpler because we are just doing plus one, any other number would require us to tweak the algorithm a bit.

### Code

    /**
    * @param {number[]} digits
    * @return {number[]}
    */
    var plusOne = function(digits) {
        const len = digits.length;
        let curry = 1;

        if(len === 0){
            return [curry];
        }
        
        for(let i = len-1; i>=0; i--){
            if(curry !== 0){
                let el = digits[i] + curry;
                if(el > 9){
                    curry = 1;
                    digits[i] = 0;
                }else{
                    curry = 0;
                    digits[i] = el;
                }
            }
        }
        
        if(curry === 1){
            digits.unshift(curry);
        }
        
        return digits;
    };

### Recursive Approach

    /**
    * @param {number[]} digits
    * @return {number[]}
    */
    var plusOne = function(digits) {
        const len = digits.length;
        if(len === 0) return [1];
        let last = len - 1;
        
        if(digits[last] === 9) {
            return plusOne(digits.slice(0, last)).concat([0]);
        }
        return digits.slice(0, last).concat([digits[last] + 1]);
    };


### Discussion

Runtime for our first solution is 48 ms which is quite fast specifically, because we are assuming a few things and making it simpler.