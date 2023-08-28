---
title: Valid Boomerang
date: 2023-08-27 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math]
---

### View *Valid Boomerang* on [LeetCode](https://leetcode.com/problems/valid-boomerang){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - Each pair in `points` must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each pair in `points` must be stored, resulting in the O(n) space complexity. However, it could be argued that it is O(1) because the input is a constant number of elements (three pairs of two).

**Runtime Beats**  
64.29% of other submissions  

**Memory Beats**  
67.95% of other sumbissions  

## Explanation  
The program implements the formula for calculating a triangle. If the input violates the rules, a triangle cannot be created, resulting in `area` equaling zero.

## Solution  

```python
class Solution:
    def isBoomerang(self, points: List[List[int]]) -> bool:
        x1, y1 = points[0]
        x2, y2 = points[1]
        x3, y3 = points[2]
        
        area = abs(x1*(y2-y3) + x2*(y3-y1) + x3*(y1-y2))/2
        return area != 0
```