---
title: Number of Segments in a String
date: 2023-05-18 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---


### View *Number of Segments in a String* on [LeetCode](https://leetcode.com/problems/number-of-segments-in-a-string/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
20 seconds

**Time Complexity**  
O(n) - The `.split()` method iterates through each element in the string, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The `.split()` method returns a list, and although we are not storing it, we still must have space for it to exist in our program temporarily, resulting in the O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
100% of other sumbissions  

## Explanation
To separate a string into segments, we can use the built-in `.split()` method, which separates each segment and returns a list of all of them. 
We will store this output in the variable `segments`.

Since the problem asks for the number of segments, we can take the output list's length and return it.

## Solution  

```python
class Solution:
    def countSegments(self, s: str) -> int:
        # Oneliner
        # return len(s.split())

        segments = s.split()

        return len(segments)
```