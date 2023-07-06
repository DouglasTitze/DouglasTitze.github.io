---
title: Hamming Distance
date: 2023-07-05 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, bit manipulation]
---

### View *Hamming Distance* on [LeetCode](https://leetcode.com/problems/hamming-distance/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n + m + k) - The algorithm iterates through all characters within both the integer inputs and their XOR representation, resulting in the O(n + m + k) time complexity.

**Space Complexity**  
O(k) - The algorithm performs XOR on both input integers and then converts the result into its binary representation; although only an intermediate value, the computer still stores this binary representation temporarily, resulting in the O(k) space complexity.

**Runtime Beats**  
91.65% of other submissions  

**Memory Beats**  
96.31% of other sumbissions  

## Explanation  
The algorithm converts the XOR of x and y into binary and counts the number of `1`s. This results in the correct output because `1` only appears if a `1` exists in one binary number and not the other at the same index.

## Solution  

```python
class Solution:
    def hammingDistance(self, x: int, y: int) -> int:
        return bin(x^y).count("1")
```