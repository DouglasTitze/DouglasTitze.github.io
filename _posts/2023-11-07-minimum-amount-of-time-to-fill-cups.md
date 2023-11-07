---
title: Minimum Amount of Time to Fill Cups
date: 2023-11-07 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math]
---

### View *Minimum Amount of Time to Fill Cups* on [LeetCode](https://leetcode.com/problems/minimum-amount-of-time-to-fill-cups/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(1) - Since the `amount` list is always 3 elements the growth rate is constant, resulting in the O(1) time complexity.

**Space Complexity**  
O(1) - You must always store 3 elements, which is a constant, resulting in the O(1) space complexity.

**Runtime Beats**  
75.60% of other submissions  

**Memory Beats**  
71.50% of other sumbissions  

## Solution  

```python
class Solution:
    def fillCups(self, amount: List[int]) -> int:
        # O(3 log 3) == O(1), since there are never more than 3 elements
        a, b, c = sorted(amount)

        # If the two smallest sum to less than c
        # Then they would either cancel out (a == b) 
        # or 
        # the remaining of b would be able to be dispensed in parallel with c
        if a + b <= c: return c
        

        # Otherwise the time is less than c, becuase you can do more than 
        # c in parallel.
        return ceil((a+b+c)/2)
```