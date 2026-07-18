---
author: "Kirti Bhardwaj"
date: 2023-11-26
linktitle: longest-substring-k-distinct
prev: /posts/median-sorted-array
title: Longest Substring with At Most K Distinct Characters
weight: 10
draft: false
---

### Problem Statement

Given a string, find the length of the longest substring T that contains at most k distinct characters.Here is the leetcode link to the problem [Longest Substring](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
Here is some discussion around it [K unique characters](https://www.geeksforgeeks.org/find-the-longest-substring-with-k-unique-characters-in-a-given-string/)

### Examples
Example 1:

    Input: s = "eceba", k = 2
    Output: 3
    Explanation: T is "ece" which its length is 3.

Example 2:

    Input: s = "aa", k = 1
    Output: 2
    Explanation: T is "aa" which its length is 2.


### Solution
This problem follows the **Sliding Window pattern**. We can use a HashMap to remember the frequency of each character we have processed. Here is one way to solve this problem:

1) Insert characters from the beginning of the string until we have ‘K’ distinct characters in the HashMap.
These characters will constitute our sliding window. We are asked to find the longest such window having no more than ‘K’ distinct characters. We will remember the length of this window as the longest window so far.

2) Keep adding one character in the sliding window.

3) In each step, try to shrink the window from the beginning if the count of distinct characters in the HashMap is larger than ‘K’. We will shrink the window until we have no more than ‘K’ distinct characters in the HashMap. This is needed as we intend to find the longest window.

4) While shrinking, decrement the frequency of the character going out of the window and remove it from the HashMap if its frequency becomes zero.

5) At the end of each step, we’ll check if the current window length is the longest so far, and if so, remember its length.

### Code
    /**
    * @param {string} s
    * @param {number} k
    * @return {number}
    */
    var lengthOfLongestSubstringKDistinct = function(s, k) {
        const uniqueChar = k;
        const len = s.length;
        
        if(len < uniqueChar+1) return len;
        
        let hMap = {}; 
        let max = 0;
        
        for(let right = 0, left = 0; right < len ; right++){
            /** Add value to map or increment **/
            hMap[s[right]] = (hMap[s[right]] || 0) + 1;

            /** 
                map size should be equal to k. 
                If not keep removing keys and increment value of left pointer
            **/
            while(Object.keys(hMap).length > uniqueChar){
                if (--hMap[s[left]] === 0) {
                    delete hMap[s[left]];
                }
                left++;
            }
        
            max = Math.max(max, right - left + 1);
        }
        
        return max;
    };


### Similar Problems

[Longest Substring Without Repeating Characters]({{< ref "longest-substring-without-repeating-char.md" >}})

[Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)