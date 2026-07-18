---
author: "Kirti Bhardwaj"
date: 2023-11-26
linktitle: longest-substring-without-repeating
prev: /posts/median-sorted-array
title: Longest Substring Without Repeating Characters
weight: 10
draft: false
---

### Problem Statement
Given a string, find the length of the longest substring without repeating characters. Let's take a look at some examples:

### Examples
***Example 1:***

    Input: "abcabcbb"
    Output: 3 
    Explanation: The answer is "abc", with the length of 3. 

***Example 2:***

    Input: "bbbbb"
    Output: 1
    Explanation: The answer is "b", with the length of 1.

***Example 3:***

    Input: "pwwkew"
    Output: 3
    Explanation: The answer is "wke", with the length of 3. 
                Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

Here is the leetcode link to the problem [ Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)


### Solution
Let's take a look at the brute force solution.
    /**
    * @param {string} s
    * @return {number}
    */
    var lengthOfLongestSubstring = function(s) {
        if(s.length < 2) return s.length;
        
        let max = Number.NEGATIVE_INFINITY ;
        
        const arr = s.split("");
        const len = arr.length;
        
        return arr.reduce((acc,item,index) => {
            let substring = [];
            
            for(let i = index; i< len; i++){
                let el = arr[i];
                if(substring.indexOf(el) != -1){
                    /** break out of loop at first repeatition **/
                    break;
                }
                substring.push(el);
                
                if(acc <= substring.length){
                    acc = substring.length;
                }
            }
            
            return acc;
        }, max);
    };

**Optimized Solution**
    /**
    * @param {string} s
    * @return {number}
    */
    var lengthOfLongestSubstring = function(s) {
        if(s.length < 2) return s.length;
        
        //Keep tracks of indexes of string characters
        const map = {};
        //left index of sliding window
        let leftIndex = 0;
        
        return s.split('').reduce((acc, el, index) => {
            //If character already exists then shift sliding window to current +1
            leftIndex = (map[el] >= leftIndex) ? map[el] + 1 : leftIndex;
            // Add current index value to map
            map[el] = index;
            // update the max value
            return Math.max(acc, index - leftIndex + 1);
        }, 0);
    };