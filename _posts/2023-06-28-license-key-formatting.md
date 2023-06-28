---
title: License Key Formatting
date: 2023-06-28 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---

### View *License Key Formatting* on [LeetCode](https://leetcode.com/problems/license-key-formatting/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - Although the input/output strings are iterated multiple times, it does not alter the growth rate, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The result stores the same number of characters as the input, resulting in the O(n) space complexity.

**Runtime Beats (Array Solution)**  
97.61% of other submissions  

**Memory Beats (String Solution)**  
98.5% of other sumbissions  

## Explanation  
The input string is reformatted to remove all `-`, convert all characters to uppercase, and reverse the string.

The input string is then iterated through in steps of k, and due to the way lists work in python, the last added string can be a variable length allowing us to satisfy that edge case. 

Example
```python
x = [1,2,3]
y = x[1:1000] # y -> [2,3]
```

Once the loop exists, return the result in reverse order.

## Array Solution  

```python
class Solution:
    def licenseKeyFormatting(self, s: str, k: int) -> str:
        res = []
        s = s.replace('-', '').upper()[::-1]

        for i in range(0,len(s),k):
            res.append(s[i:i+k])

        return '-'.join(res)[::-1]
```

## String Solution  

```python
class Solution:
    def licenseKeyFormatting(self, s: str, k: int) -> str:
        res = ""
        s = s.replace('-', '').upper()[::-1]

        for i in range(0,len(s),k):
            if res != "":
                res = res + "-" + s[i:i+k]
            else:
                res = s[i:i+k]

        return res[::-1]
```