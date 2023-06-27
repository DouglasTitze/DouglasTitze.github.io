---
title: Intersection of Two Arrays
date: 2023-06-26 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table, pythonic]
---

### View *Intersection of Two Arrays* on [LeetCode](https://leetcode.com/problems/intersection-of-two-arrays/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n + m) - Although multiple operations are mutating the input lists, none are nested, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n + m) - The algorithm creates two sets of at most `n` and `m` elements, resulting in the O(n + m) space complexity.

**Runtime Beats**  
79.72% of other submissions  

**Memory Beats**  
69.72% of other sumbissions  

## Explanation  
The steps to this algorithm are:
*   Convert each input list into a set
*   Execute the intersection function
    *    Under the hood it checks if each number from the set of nums1 is within the set of nums2
    *    If ever true, it begins creating a set of their intersection


## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view


## Solution  

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return set(nums1).intersection(set(nums2))
```