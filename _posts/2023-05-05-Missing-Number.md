---
title: Missing Number
date: 2023-05-05 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, math]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/missing-number/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I created a solution quickly that was both fast and space efficient.

# Algorithm Description

**Gauss Sum -** Outputs the sum of all numbers from 0 - n $$n(n+1)\over 2$$

# Solution Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n) - Every element in nums must be iterated over once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - One variable was created and the number of variables created does not depend on n, resulting in the O(1) space complexity.

**Runtime Beats**  
86.63% of other submissions  

**Memory Beats**  
88.74% of other sumbissions  

# Solution  

```python
class Solution(object):
    def missingNumber(self, nums):
        n = len(nums)
        
        # Gauss Sum - n * (n + 1) / 2)
        return int(n * (n + 1) / 2) - sum(nums)
```
