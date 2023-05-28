---
title: Add Digits
date: 2023-05-27 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math, string]
---


### View *Add Digits* on [LeetCode](https://leetcode.com/problems/add-digits/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
3 minutes

**Time Complexity**  
O(1) - The static number of operations performed is independent of n, resulting in the O(1) time complexity.

**Space Complexity**  
O(1) - No variables are created to determine the output, resulting in the O(1) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
96.06% of other sumbissions  

## Explanation
If the input is divisible by 9 and not equal to 0, then the output will eventually equal 9.  

Elsewise, the number will eventually become the be the remainder.

## Solution  

```python
class Solution:
    def addDigits(self, num: int) -> int:
        if num % 9 == 0 and num != 0:
            return 9        
        return num % 9      
```