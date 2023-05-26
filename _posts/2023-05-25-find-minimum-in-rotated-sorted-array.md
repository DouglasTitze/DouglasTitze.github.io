---
title: Find Minimum in Rotated Sorted Array
date: 2023-05-25 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search]
---


### View *Find Minimum in Rotated Sorted Array* on [LeetCode](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
_____TIME_HERE_____ minutes

**Time Complexity**  
O(log n) - We are performing a modified version of binary search, and when binary search is performed on a sorted array, the time complexity is O(log n).

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

## Explanation
Before performing a binary search, we must initialize our left and right variables; `l` to "point" at element 0 and `r` to "point" at the last element.

We start and continue the `while` loop until `l` is larger than `r.` Inside the loop, we initialize `m` to the middle of `l` and `r`.

*   If the number at `m` is larger than the number at `r`, then `m` is inside of the pivoted portion of the list, meaning there will not be any elements less than the one at `m` to the left of element `m`. 
Therefore, we must search the right side of the list, and we do this by `l = m + 1`.

*   If the number at `m` does not meet the previous condition, then we are in the sorted portion of the list and can move our right pointer to the left, `r = m`.

Once our `while` loop exits, we have found the minimum element at our right pointer `r` and can simply return it.

## Algorithm Description

**Binary Search Algorithm -** A sorting algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l = 0
        r = len(nums) - 1

        while l < r:

            m = (l+r)//2

            if nums[m] > nums[r]: l = m + 1
            else: r = m 

        return nums[r]
```