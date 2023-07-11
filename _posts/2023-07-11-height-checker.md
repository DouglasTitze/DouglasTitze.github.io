---
title: Height Checker
date: 2023-07-11 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, counting]
---

### View *Height Checker* on [LeetCode](https://leetcode.com/problems/height-checker/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n log n) - The sort function dominates the complexity of all other operations, resulting in the O(n log n) time complexity.

**Space Complexity**  
O(n) - The sorted array must be temporarily stored before zipping with the original input array, resulting in the O(n) space complexity.

**Runtime Beats**  
63.79% of other submissions  

**Memory Beats**  
70.41% of other sumbissions  

## Explanation  

The algorithm simultaneously increments through the sorted and input lists using the `zip` function. Then it increments the `differences` variable when the elements are not equal.

## Solution  

```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        differences = 0

        for h, s_h in zip(heights, sorted(heights)):
            if h != s_h:
                differences += 1

        return differences
```