---
title: Relative Sort Array
date: 2023-09-04 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, hash map]
---

### View *Relative Sort Array* on [LeetCode](https://leetcode.com/problems/relative-sort-array/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n + m) - All of the elements from `arr1` (n) and `arr2` (m) must be visited, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n + m) - In the worst case, all elements are unique from both input lists, resulting in the O(n + m) space complexity.

**Runtime Beats**  
94.25% of other submissions  

**Memory Beats**  
59.20% of other sumbissions  

## Explanation  
_The comments explain the program_

## Data Structures Used  

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

## Solution  

```python
class Solution:
    def relativeSortArray(self, arr1: List[int], arr2: List[int]) -> List[int]:
        # Count the frequency of each number from arr1
        dic = defaultdict(int)
        for n in arr1:
            dic[n] += 1

        # Populate the result array with all elements in arr2 + their appearances from arr1
        res = []
        for n in arr2:
            if n in dic:
                res += [n] * dic.pop(n)
            else:
                res += n

        # Populate the leftover array with all the numbers from arr1 that were not in arr2
        leftover = []
        for k,v in dic.items():
            leftover += [k]*v

        # Return the final result array combined with the sorted leftover array
        return res + sorted(leftover)
```