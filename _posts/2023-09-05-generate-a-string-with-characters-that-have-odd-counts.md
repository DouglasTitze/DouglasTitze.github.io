---
title: Generate a String With Characters That Have Odd Counts
date: 2023-09-05 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math, string]
---

### View *Generate a String With Characters That Have Odd Counts* on [LeetCode](https://leetcode.com/problems/generate-a-string-with-characters-that-have-odd-counts/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
3 minutes

**Time Complexity**  
O(n) - The construction of the string takes O(n) time, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - If the result string is counted in the space complexity, then the space complexity is O(n), otherwise it is O(1).

**Runtime Beats**  
98.43% of other submissions  

## Explanation  
_The comments explain the program_

## Solution  

```python
class Solution:
    def generateTheString(self, n: int) -> str:
        # If n is odd, return `a` n times
        if n%2 != 0:
            return 'a' * n

        # Otherwise return `a` n-1 times and `b`
        else:
            return 'a' * (n - 1) + 'b'
```