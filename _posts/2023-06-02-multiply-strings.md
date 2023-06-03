---
title: Multiply Strings
date: 2023-06-02 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, math, string]
---


### View *Multiply Strings* on [LeetCode](https://leetcode.com/problems/multiply-strings/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n+m) - We must iterate through all the characters from both input strings, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n+m) - Since we are converting both input strings to integers, and then back we must have enough space to hold the intermediate values of each conversion, resulting in the O(n+m) space complexity.

**Runtime Beats**  
92.66% of other submissions  

**Memory Beats**  
97.94x% of other sumbissions  

## Explanation
To multiply `num1` and `num2` together, we must convert them to integers (`int()`) and then multiply them. 

After this we must convert the result to a string (`str()`).

Once converted we return the output.

## Solution  

```python
class Solution:
    def multiply(self, num1: str, num2: str) -> str:
        return str(int(num1)*int(num2))
```