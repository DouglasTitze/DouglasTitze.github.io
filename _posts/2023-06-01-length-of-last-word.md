---
title: Length of Last Word
date: 2023-06-01 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, pythonic]
---


### View *Length of Last Word* on [LeetCode](https://leetcode.com/problems/length-of-last-word/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n) - Each character in the string is visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each grouping of non-whitespace characters is returned in a list; in the worst case, that list would contain n/2 elements.
Since multiples of a growth rate are ignored, the reported space complexity is O(n).

## Explanation
The `.split()` method removes all whitespace and returns a list of characters separated by white space ("w o    w  " returns ["w","o","w"]). 

We then access the last element in the list ([-1]) and return the length of it.

## Solution  

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        return len(s.split()[-1])
```