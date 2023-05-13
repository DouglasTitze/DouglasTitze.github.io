---
title: To Lower Case
date: 2023-05-12 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/to-lower-case/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
The solution was simple and intuitive.

# Solution Statistics  

**Time Spent Coding**  
10 seconds

**Time Complexity**  
O(n) - Each element of the input string must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - We are not creating new variables, resulting in the O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
100% of other sumbissions  

# Solution  

```python
class Solution:
    def toLowerCase(self, s: str) -> str:
        return s.lower()
```
