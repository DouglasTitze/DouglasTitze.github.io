---
title: Longest Arithmetic Subsequence of Given Difference
date: 2023-11-05 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash table, dynamic programming]
---

### View *Longest Arithmetic Subsequence of Given Difference* on [LeetCode](https://leetcode.com/problems/longest-arithmetic-subsequence-of-given-difference/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n) - Each element in the array must be visisted, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each element in the array must be stored in the dictionary, resulting in the O(n) space complexity.

**Runtime Beats**  
91.64% of other submissions  

## Explanation  
For each element in the array, check if its ancestor (`n - diff`) is in the dictionary, if not then add it with a value of 1, if it is then increment its ancestors value by 1. 
Doing this repeatedly for each value in the array allows us to dynamically update subsequences, becuase if multiple element are within the same subsequence they will incrementally increase as each new element in the subsequence is discovered.

## Data Structure Used  

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view

## Solution  

```python
class Solution:
    def longestSubsequence(self, arr: List[int], difference: int) -> int:
        dic = {}

        for n in arr:
            if n - difference not in dic:
                dic[n] = 1
            else:
                dic[n] = dic[n - difference] + 1

        return max(dic.values())
```