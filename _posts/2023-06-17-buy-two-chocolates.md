---
title: Buy Two Chocolates
date: 2023-06-17 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array]
---

### View *Buy Two Chocolates* on [LeetCode](https://leetcode.com/problems/buy-two-chocolates/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - Three O(n) operations are performed, but big-O represents the growth rate and not the exact multiple of that growth rate, resulting in only an O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the inputs, resulting in the O(1) space complexity.

**Runtime Beats**  
88.97% of other submissions  

**Memory Beats**  
85.59% of other sumbissions  

## Explanation  
Extract the minimum value, store it in `min1,` and then remove that element.
Extract the other minimum value and store it in `min2`.
Compute the result (`res`) of how much money will be left over after purchasing both chocolates.
*   If this value is greater than or equal to zero, this is a valid purchase; return the remaining money `res`.
*   If the result is invalid, return money.

## Solution  

```python
class Solution:
    def buyChoco(self, prices: List[int], money: int) -> int:
        min1 = min(prices)
        prices.remove(min1)
        min2 = min(prices)
        res = money - (min1+min2)

        if res >= 0: return res
        else:        return money
```