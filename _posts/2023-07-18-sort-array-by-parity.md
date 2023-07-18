---
title: Sort Array By Parity
date: 2023-07-18 00:00:00 -400
categories: [Coding Questions, easy]
tags: [python, array]
---

### View *Sort Array By Parity* on [LeetCode](https://leetcode.com/problems/sort-array-by-parity/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - Every element in the input list must be seen, resulting in the O(b) time complexity.

**Space Complexity**  
O(n) - Every element in the input list is duplicated and placed in either `evens` or `odds,` resulting in the O(n) space complexity.

**Runtime Beats**  
99.69% of other submissions  

**Memory Beats**  
51.77% of other sumbissions  

## Explanation  
For every element `n` in nums, if the modulo of 2 is larger than 0, append that number to the odds list; else append `n` to evens.

Finally, return the combination of both lists.

## Solution  

```python
class Solution:
    def sortArrayByParity(self, nums: List[int]) -> List[int]:
        evens = []
        odds = []

        for n in nums:
            if n%2:
                odds.append(n)
            else:
                evens.append(n)

        
        return evens + odds
```