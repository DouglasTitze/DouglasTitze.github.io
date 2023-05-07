---
title: Positions of Large Groups
date: 2023-05-06 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [string, sliding window]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/positions-of-large-groups/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew immediately what algorithm to use and how to implement it.

# Algorithm Description

**Sliding Window Technique -** An algorithm that takes a subset of data from an iterable object and expands or reduces that subset based on given conditions.

**Visual Examples**  
An intense dive into the sliding window technique can be found here, [click](https://www.youtube.com/watch?v=jM2dhDPYMQM){:target="_blank"} to view  
Unfortunately, all the other resources I found that spoke about the sliding window technique covered only some of its use cases.

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - In the worst-case scenario, each element gets visited twice, but since the increase in time is still linear, aka big O ignores content multiples of n, it still leaves us with an O(n) time complexity.

**Space Complexity**  
O(n) - In the worst-case scenario, the entire string will be partitioned into equal parts of "large" groups making us store n/3 intervals, resulting in the O(n) space complexity because, as stated in the last problem, the increase in space usage is still linear despite it being divided by 3.

**Runtime Beats**  
80.72% of other submissions  

**Memory Beats**  
98.80% of other sumbissions  

# Solution  

```python
class Solution(object):
    def largeGroupPositions(self, s):
        if len(s) < 3: return []

        # Left and right "pointers"
        l, r = 0, 1

        groups = []

        while r < len(s):
            
            # If the left and right characters match, continue as normal
            # and skip the rest of the while loop
            if s[l] == s[r]: 
                r += 1
                continue

            # If the left and right characters do NOT match, then check
            # If the group is large, if it then appends it to the output list
            if r-l > 2:            
                groups.append([l,r-1])

            l = r
            r += 1
        
        # Edge case: Check for an extra group at the end of the while loop
        if r-l > 2:            
            groups.append([l,r-1])

        return groups
```
