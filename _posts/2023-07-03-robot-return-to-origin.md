---
title: Robot Return to Origin
date: 2023-07-03 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---

### View *Robot Return to Origin* on [LeetCode](https://leetcode.com/problems/robot-return-to-origin/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
3 minutes

**Time Complexity**  
O(n) - The entire input list must be iterated through, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables declared is constant and independent from the input list, resulting in the O(1) space complexity.

**Runtime Beats**  
57.93% of other submissions  

**Memory Beats**  
69.80% of other sumbissions  

## Explanation  
The algorithm works similarly to a math problem; it adds and subtracts from an `x` and `y` variable according to the move, `U` being `y += 1` and so on.

Finally, it compares if the x and y values equal zero and returns that result.

## Solution  

```python
class Solution:
    def judgeCircle(self, moves: str) -> bool:
        x,y = 0,0

        for m in moves:
            if   m == "U": y +=1
            elif m == "D": y -=1
            elif m == "R": x +=1
            else:          x -=1

        return x == 0 and y == 0
```