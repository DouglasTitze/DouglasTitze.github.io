---
title: Ugly Number
date: 2023-05-28 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math]
---


### View *Ugly Number* on [LeetCode](https://leetcode.com/problems/ugly-number/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(log n) - The maximum number of divisions is log base [2,3, or 5] of n, resulting in the O(log n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
100% of other sumbissions  

## Explanation
We must eliminate all the inputs that violate the solution space to avoid incorrect results. 
All values less than one must return `False` according to the problem, so we execute `if n < 1: return False` to eliminate these inputs and return the correct answer.

After this, we enter a `for` loop and perform repetitive division (inside of the `while` loop) on the input number `n` until the current prime number is no longer a factor of `n`.

Once we exit the `for` loop, we `return n==1`.
*   If `False`, then the prime numbers were not factors of `n`.
*   If `True`, then one or more prime numbers were factors of `n`, leaving `n` equaling one.

## Solution  

```python
class Solution:
    def isUgly(self, n: int) -> bool:
        if n < 1: return False

        for div in [2, 3, 5]:
            while n%div == 0:
                n = n//div
                
        return n==1
```