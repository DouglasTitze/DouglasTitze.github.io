---
title: Number of Laser Beams in a Bank
date: 2023-04-19 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, math, string, matrix]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/number-of-laser-beams-in-a-bank/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I did not overcomplicate the problem despite the description presenting the problem in a more difficult manner.

# Solution Statistics  

**Time Spent Coding**  
8 minutes

**Time Complexity**  
O(n * m) - The number of rows is m, and the number of cells in each row is n. 
We must traverse every element in the matrix, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - We only create three variables; since this number does not depend on n or m, the space complexity is O(1).

**Runtime Beats**  
99.32% of other submissions  

**Memory Beats**  
99.32% of other sumbissions  

# Solution  

```python
class Solution:
    def numberOfBeams(self, bank: List[str]) -> int:
        # Number of devices on the previous row
        tot = prev = 0

        for row in bank:

            # Number of devices on the current row
            cur = row.count("1")
            
            # If there was at least one device, then
            # add its lasers to the total
            if cur:
                tot += cur * prev
                prev = cur

            # If there are no security devices on the current
            # row, then we do not need to reset the prev
            # else: continue
            
        return tot
```
