---
author: "Kirti Bhardwaj"
date: 2023-11-24
linktitle: array-diagonal-diff
prev: /posts/median-sorted-array
title: Arrays in JS- Diagonal Difference
weight: 10
draft: false
---

### Problem Statement

Given a square matrix, calculate the absolute difference between the sums of its diagonals.
Here is the link to problem [HackerRank](https://www.hackerrank.com/challenges/diagonal-difference/problem).


**Example**

    1 2 3
    4 5 6
    9 8 9 

The left-to-right diagonal = 1+5+9=15. The right to left diagonal = 3+5+9=17. Their absolute difference is |15-17| = 2.


### Solution
Let's take an example:

    11 2 4
    4 5 6
    10 8 -12


If we notice a pattern emerges. Our primary diagonal values are 11,5 and -12 that is if our input is a 2d integer array our primary diagonal values will be [[0,0],[1,1],[2,2]].
Similarly, for our secondary diagonal values are [[0,2],[1,1],[2,0]] that is 4,5 and 10.

Now, if we loop through array our primary values are where i = j. And secondary values can be defined as i+j = len-1; where length is length of the array.Let's look at the code:

### Code
    function diagonalDifference(arr) {
        let primarySum = 0;
        let secondarySum = 0;
        const len = arr.length;

        for(let i = 0; i < len; i++){
            let dArr = arr[i];
            for(let j = 0; j < dArr.length; j++){
                if(i === j){
                    primarySum += arr[i][j];
                }
                if(i+j === len-1){
                    secondarySum += arr[i][j];
                }
            }
        }

        return Math.abs((primarySum - secondarySum));
    }