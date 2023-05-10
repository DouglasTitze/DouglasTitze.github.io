---
title: Valid Anagram
date: 2023-05-10 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash map, string]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/valid-anagram/){:target="\_blank"} on LeetCode

# My Thoughts

**What Went Well**  
I knew how to approach the problem in multiple ways and implemented them all quickly.

# Data Structure Description

**Hash Map (Dictionary) -** A data structure that stores a collection of keys, each to their respective values.
Each key may only appear once.

# Solution Statistics

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n + m) - In the worst-case scenario, we must iterate through the entire length of `t`, assigning it to have a length of m, resulting in the O(n + m) time complexity.
We do not remove the m from the time complexity because it is not a constant and depends on the user's input. 
It may be much larger than n, significantly affecting the time complexity.

**Space Complexity**  
O(n) - We will, at most, store n elements, where n is the length of input string `s`, resulting in the O(n) space complexity.

**Runtime Beats**  
79.51% of other submissions

**Memory Beats**  
98% of other sumbissions

# Solution

```python
class Solution(object):
    def isAnagram(self, s, t):
        # If s is longer than t, this code eliminates that edge case
        if len(s) != len(t): return False

        # character in s = frequency in s
        charS = {}

        # For the current character in string s, execute the code block
        for c in s:
            # Increment the current characters value by 1
            charS[c] = charS.get(c,0) + 1

        # For the current character in string t execute the code block
        for c in t:
            # Check if the current characters value is equal to 0
            # If a character is not in the dictionary, then default to 0
            if charS.get(c,0) == 0:
                return False

            charS[c] -= 1

        return True
```
