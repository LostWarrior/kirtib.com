---
author: "Kirti Bhardwaj"
date: 2023-05-11
linktitle: median-sorted-array
prev: /posts/cors
title: Arrays in JS- Median of two sorted arrays
weight: 10
draft: false
---

### Problem Statement

There are two sorted arrays nums1 and nums2 of size m and n respectively.
Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

Here is the leetcode link to the problem: [LeetCode: Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)

 ***What is a median?***

[StatTrek](https://stattrek.com/statistics/dictionary.aspx?definition=median) defines median as a measure of central tendency. Simply explained In an array of odd values median will be middle value.

 ***Discussion***

We are trying to find union of two arrays A and B here, left half will be smaller than right half. Finding median gives use left half which ends with median value. 
Merging two arrays take O(m+n) time. We need to find a way where we can find the values in left half without merging both arrays so, as to keep complexity lower than O(m+n)

Read more on [Polya's problem solving pdf](https://math.berkeley.edu/~gmelvin/polya.pdf)


### Test Cases:

nums1 = [1, 3]
nums2 = [2]
union = [1,2,3]

The median is 2.0


nums1 = [1, 2]
nums2 = [3, 4]
union = [1,2,3,4]

The median is (2 + 3)/2 = 2.5


### Solution:

We will use binary search to find the left half of the union such that, both halves are equal size and every element in left half is lesser than every element in right half. We know the size of this would be (m + n)/2, so we can safely say that we only want to know what values array1 will be contributing. Because, we know array2 would be contributing rest of the values.

Let's try to solve this:

array x => [x1,x2,x3,x4,x5,x6]; <br>
array y => [y1, y2, y4, y4, y5, y6, y7, y8];

Let's say we find a partition x => (2, 4) and y => (5, 3) that is, on left side of union array we will have:
x1,x2,y1,y2,y3,y4,y5 and on right side we will have x3,x4,x5,x6,y6,y7,y8.

Now if, x2 <= y6 (largest) && y5 <= x3 (smallest) then our median will be <br>
if numbers are ***even*** => median = avg(max(x2,y6), min(x3,y5)) <br>
if numbers are ***odd*** => median = max(x2,y5); (one extra element on left side)

To find this partition we do a binary search on smaller of two arrays.Time complexity of this operation would be O(log(min(x,y))) where x and y are lengths of two arrays.


Example:
***Total Size Odd***

Everything becomes clearer once we look at examples. So, let's take two arrays A and B where total number is odd.

A= [1,3,8,9,15]; <br>
B= [7,11,18,19,21,25];

U = [1,3,7,8,9, **11**,15,18,19,21,25] where, 11 is our median.

Let's look at pseudocode:

    1) partitionX + partitionY = (x+y+1)/2; // +1 to handle both odd and even cases
    2) Three cases:
        a) Found: (maxLeftX <= minRightY) && (maxLeftY <= minRightX);
        b) else if (maxLeftX > minRightY) => move towards left in X
        c) else move towards right in X


Start = 0; end = 4 (A.length) therefore,
partitionX = (start + end)/2 = (0+4)/2 = 2;
partitionY = (x+y+1)/2  - partitionX= ((5+6+1)/2)-2 = 4;


So, we partition X at 2 and Y at 4. This makes our two arrays look like this:
leftX = [1,3] & leftY = [7,11,18,19]
rightX = [8,9,15] & rightY = [21,25]
Because, total size of array is odd we have one extra element on left.

Now, maxLeftX[3] <= minRightY[21] => true && maxLeftY[19] <= minRightX[8] => false;
We move binary search towards right in X.

So, new start = partitionX +1 = 2 + 1 = 3;
new partitionX = (start + end)/2 = (3+4)/2 = 3;
new partitionY = (x+y+1)/2 - partitionX = ((5+6+1)/2)-3 = 3;

leftX = [1,3,8] & leftY = [7,11,18]
rightX = [9,15] & rightY = [19,21,25]

Now, maxLeftX[8] <= minRightY[19] => true && maxLeftY[18] <= minRightX[9] => false;
we move binary search towards right in X.

Start = 4; partitionX = 4; partitionY = 2;

leftX = [1,3,8,9] & leftY = [7,11]
rightX = [15] & rightY=[18,19,21,25]

Now, maxLeftX[9] <= minRightY[18] => true && maxLeftY[11]<= minRightX[15] => true;

So, our median = max(maxLeftX,maxLeftY) = max(9,11) = **11**;

***Total Size Even***

A= [23,26,31,35]; <br>
B= [3,5,7,9,11,16];

U = [3,5,7,9, **11,16**, 23,26,31,36] where median is (11+16)/2 = 13.5

Start = 0; end = 4 (A.length) therefore,
partitionX = (start + end)/2 = (0+4)/2 = 2;
partitionY = (x+y+1)/2  - partitionX= ((4+6+1)/2)-2 = 3;

So, we partition X at 2 and Y at 3. This makes our two arrays look like this:
leftX = [23,26] & leftY = [3,5,7]
rightX = [31,35] & rightY = [9,11,16]

Now, maxLeftX[26] <= minRightY[9] => false so, we move binary search towards left in X.

Start = 0; end = partitionX -1 = 2-1;
partitionX = (start + end)/2 = (0+1)/2 = 0;
partitionY = (x+y+1)/2  - partitionX= ((4+6+1)/2)-0 = 5;


So, we partition X at 1 and Y at 4. This makes our two arrays look like this:
leftX = [] & leftY = [3,5,7,9,11]
rightX = [23,26,31,35] & rightY = [16]

Now, maxLeftX[-Infinity] <= minRightY[16] => true && maxLeftY[11] <= minRightX[23] => true

**median = avg(max(maxLeftX,maxLeftY), min(minRightY,minRightX))**
median = avg(max(-Infinity,11), min(16,23)) = avg(11,16) = 13.5


### Code: 
    /**
    * @param {number[]} nums1
    * @param {number[]} nums2
    * @return {number}
    */
    var findMedianSortedArrays = function(nums1, nums2) {
        const len = nums1.length + nums2.length;
        let A = (nums1.length > nums2.length) ? nums2 : nums1;
        let B = (nums1.length > nums2.length) ? nums1 : nums2;
        
        const x = A.length; 
        const y = B.length;
        let start = 0, end = A.length, half = (x + y + 1)/2;
        
        while (start <= end){
            let partitionX = (start+end)/2;
            let partitionY = half - partitionX;
            
            //Two partition of X
            let maxLeftX = (partitionX === 0)? Number.MIN_SAFE_INTEGER : A[partitionX -1];
            let minRightX = (partitionX === x) ? Number.MAX_SAFE_INTEGER : A[partitionX];
            
            //Two partitions of Y
            let maxLeftY = (partitionY === 0)? Number.MIN_SAFE_INTEGER : B[partitionY -1];
            let minRightY = (partitionY === y) ? Number.MAX_SAFE_INTEGER : B[partitionY];
            
            //If partitions are correct
            if((maxLeftX <= minRightY) && (maxLeftY <= minRightX)){
                if(len%2 === 0){
                    //If final length is even
                    return (Math.max(maxLeftX,maxLeftY)+ Math.min(minLeftX,minLeftY))/2;
                }else{
                    //If final length is odd
                    return Math.max(maxLeftX, maxLeftY);
                }
            }else if(maxLeftX > minRightY){
                //move towards left
                end = partitionX - 1;
            }else{
                //move towards right
                end = partitionX + 1;
            }
        }
        
    };


### Another Approach

    var findMedianSortedArrays = function(A, B) {
        const XLen = A.length;
        const YLen = B.length;
        const len = XLen + YLen;

        let arr = [];
        /** If single element in final array return that **/
        if(len === 1){
            return (XLen === 1) ? A[0]: B[0];
        }
        
        let pivot = (len % 2 === 0) ? (len/2) + 1 : Math.ceil(len/2);
        let i = 0; let j = 0
        
        while(arr.length < pivot){
            if(i< XLen && j < YLen ){
                if(A[i] <= B[j]){
                    arr.push(A[i]);
                    i++;
                }else{
                    arr.push(B[j]);
                    j++;
                }
                
            }else if(i >= XLen){
                arr.push(B[j]);
                j++;
            }else{
                arr.push(A[i]);
                i++;
            }
        }
        
        return (len%2 === 0) ? (arr[arr.length-1] + arr[arr.length-2])/2 : arr[arr.length-1];
    };

### Reference:

[Youtube: Median of sorted arrays](https://www.youtube.com/watch?v=CMjAo8_8JYM)

[Medium: Finding the Median of 2 Sorted Arrays in Logarithmic Time](https://medium.com/@hazemu/finding-the-median-of-2-sorted-arrays-in-logarithmic-time-1d3f2ecbeb46)

[Youtube: Median of two sorted arrays of different sizes.](https://www.youtube.com/watch?v=LPFhl65R7ww)
