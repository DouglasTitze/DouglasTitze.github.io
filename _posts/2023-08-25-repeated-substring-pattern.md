---
title: Repeated Substring Pattern
date: 2023-08-25 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---

### View *Repeated Substring Pattern* on [LeetCode](https://leetcode.com/problems/repeated-substring-pattern/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - The input string `s` is duplicated and iterated multiple times, but big-O does not consider this when calculating time complexity, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The input string must be duplicated, resulting in the O(n) space complexity. Technically, it stores `n * 2` characters since `s` is repeated twice in the duplicated string, but as stated before, this factor is not considered.

**Runtime Beats**  
63.28% of other submissions  

**Memory Beats**  
72.18% of other sumbissions  

## Explanation  
The algorithm attempts to find the original input string within the duplicated string `repeated`. 
To avoid false positives, remove the first and last character from the `repeated` string. This allows for a single unique repeated pattern to be found. But, if the string is inconsistent with repeating substrings, removing the first and last characters will cause the program to return false.

## Solution  

```python
class Solution:
    def repeatedSubstringPattern(self, s: str) -> bool:
        repeated = s + s
        return s in repeated[1:]
```