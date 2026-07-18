---
author: "Kirti Bhardwaj"
date: 2023-11-28
linktitle: sliding-window-pattern
prev: /posts/median-sorted-array
title: Problem Solving Patterns => Sliding Window
weight: 10
draft: false
---

### Sliding Window Pattern 

In a lot of problems we are expected to find something among all the contiguous subarrays.A brute force way is to loop over the elements again and again till we find the result. This type of problem can be solved in a more optimized way by maintaining a window which satisfies problem constraints.This window can be increased or decreased based on the changing constraints and inputs.

There is good discussion to follow on leetcode about this specific pattern [leetcode](https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/sliding-window-algorithm-template-to-solve-all-the-leetcode-substring-search-problem)

Let's take a look at [some problems](https://leetcode.com/tag/sliding-window/) which can be solved using this:

###  Longest Substring with At Most Two Distinct Characters
For a discussion about this please check [Longest Substring with At Most K Distinct Characters]({{< ref "longest-substring-k-distinct.md" >}})


### Longest Substring Without Repeating Characters
For a discussion about this please check [Longest Substring Without Repeating Characters]({{< ref "longest-substring-without-repeating-char.md" >}})


### Minimum Window Substring

Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).

Example:

    Input: S = "ADOBECODEBANC", T = "ABC"
    Output: "BANC"
    
Note:
If there is no such window in S that covers all characters in T, return the empty string "".
If there is such window, you are guaranteed that there will always be only one unique minimum window in S.

Here is a link to the [problem](https://leetcode.com/problems/minimum-window-substring/)
And here is a link to the ways to solve it [solution](https://leetcode.com/articles/minimum-window-substring/)

**Solution**
    /**
    * @param {string} s
    * @param {string} t
    * @return {string}
    */
    var minWindow = function(s, t) {
        const slen = s.length;
        const tlen = t.length;
        if(slen === 0 || tlen === 0){
            return "";
        }
        
        let hMap = {};
        
        /** Create a map which keeps count of all unique characters in t **/
        for(let i = 0; i < tlen; i++){
            hMap[t.charAt(i)] = (hMap[t.charAt(i)] || 0) +1;
        }
        /** initialize sliding window */
        let counter = Object.keys(hMap).length;
        let left = 0; let right = 0; let head = 0;
        let min = Number.POSITIVE_INFINITY;

        while(right < slen){
            let c= s.charAt(right);
            // if current character is in hashMap, decrement count
            if(hMap.hasOwnProperty(c)){
                hMap[c] = hMap[c] - 1;
                if(hMap[c] === 0){
                    counter--;
                }
            }
            
            right++;
            /** So we are basically assuring that every unique character in substring
                exists in string1 as many times as it exists in substring by maintaining a counter. 
                if counter = 0, string1 has all chars of substring
            **/
            while(counter === 0){
                let temp = s.charAt(left);
                if(hMap.hasOwnProperty(temp)){
                    hMap[temp] = hMap[temp]+1;
                    if(hMap[temp] > 0){
                        counter++;
                    }
                }
                /**
                    Whenever counter = 0 we have a valid candidate for our ans, 
                    but we update ans only if it is shorter than previously recorded minimum length ans.
                **/
                if(right-left < min){
                        min = right - left;
                        head = left;
                }
                left++;
            }
            
            
        }
        
        if(min == Number.POSITIVE_INFINITY) return "";
        return s.substring(head, head+min);
        
    };

###  Find All Anagrams in a String
Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.

Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.

The order of output does not matter. Here is the leetcode link to the problem [leetcode](https://leetcode.com/problems/find-all-anagrams-in-a-string/)


Example 1:

    Input:
    s: "cbaebabacd" p: "abc"

    Output:
    [0, 6]

    Explanation:
    The substring with start index = 0 is "cba", which is an anagram of "abc".
    The substring with start index = 6 is "bac", which is an anagram of "abc".

Example 2:

    Input:
    s: "abab" p: "ab"

    Output:
    [0, 1, 2]

    Explanation:
    The substring with start index = 0 is "ab", which is an anagram of "ab".
    The substring with start index = 1 is "ba", which is an anagram of "ab".
    The substring with start index = 2 is "ab", which is an anagram of "ab".

**Solution**
    Exactly the same as above with the added condition that the substring should be of length equal to p and that we have to return indexes of all such occurrences.

    /**
    * @param {string} s
    * @param {string} p
    * @return {number[]}
    */
    var findAnagrams = function(s, p) {
        const slen = s.length;
        const plen = p.length;
        if(slen < plen || slen === 0) {return []};
        
        let hMap = {};let arr = [];
        p.split("").map((el) =>{
            hMap[el] = (hMap[el] || 0) +1;
        });
        
        let left = 0; let right = 0; let stringSize = plen;
        let counter = Object.keys(hMap).length;
        
        while(right < slen){
            let c = s[right];
            
            /** Decrement the counter; if current character is in hashMap**/
            if(hMap.hasOwnProperty(c)){
                hMap[c] = hMap[c] -1;
                if(hMap[c] === 0){ counter--;}
            }
            
            right++;
            /** if counter == 0, means we found an answer, 
                now try to trim that window by sliding left to right.
            **/
            while(counter === 0){
                if(right-left === stringSize){
                    arr.push(left);
                }
                
                let cStart = s.charAt(left);
                
                /** Increment the counter **/
                if(hMap.hasOwnProperty(cStart)){
                    hMap[cStart] = hMap[cStart] + 1;
                    if(hMap[cStart] > 0) { counter++; }
                }
                
                left++;
                
            }
            
        }
        
        return arr;
    };

There are other problems that can be solved using this pattern which will cover in other posts.
