---
title: Kth Missing Positive Number
date: 2023-08-28 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table]
---

### View *Kth Missing Positive Number* on [LeetCode](https://leetcode.com/problems/kth-missing-positive-number/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n + k) - Each element in the list must be visited on top of k elements if the entire list is increasing from 1 to n, resulting in the O(n + k) time complexity.

**Space Complexity**  
O(n) - When converting a list to a set, the list is not replaced until the set is full created, resulting in the O(n) space complexity, but technically only a bit of extra space is created except for a brief moment.

**Runtime Beats**  
92.14% of other submissions  

## Explanation  
The list is converted into a set, and then a for loop iterates from 1 to the length of the list plus k plus 1. This accommodates for all elements in every worst-case scenario. This allows for simple checks at each element, allowing the program to return the current number when k equals 0.

## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view


## Solution  

```python
class Solution:
    def findKthPositive(self, arr: List[int], k: int) -> int:
        arr = set(arr)
        for num in range(1, len(arr)+k+1):
            if num not in arr:
                k -= 1
            if k == 0:
                return num
```