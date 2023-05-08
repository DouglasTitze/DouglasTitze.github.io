---
title: Isomorphic Strings
date: 2023-04-23 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash map, string]
---

# Links  

Go to the [solution](#solution)  
Go to the [question](https://leetcode.com/problems/isomorphic-strings/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew to use a different map for each string, but not in such a unique way.

**What Went Wrong**  
I did not fully understand the constraints resulting in an incorrect approach to the problem.

**How I Can Improve**  
I further analyze the constraints to ensure a proper understanding of the problem before approaching it.

# Data Structure Description

**Hash Map (Dictionary) -** A data structure that stores a collection of keys, each to their respective values. 
Each key may only appear once. 

# Solution Statistics  

**Time Complexity**  
O(n) - We are iterating through both strings simultaneously, and each string's length is equal to n, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst case, we store all n elements of both strings, resulting in an O(2 * n) space complexity.
Since we ignore constant multiples of n, we reduce the space complexity to O(n).

**Runtime Beats**  
99.98% of other submissions  

**Memory Beats**  
99.99% of other sumbissions  

# Solution  

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        Ds = {}
        Dt = {}
        
        for i in range(len(s)):

            # If the current character of s and t is not in either dictionary
            if s[i] not in Ds and t[i] not in Dt:
                # Map the current character to the other string's current character
                Ds[s[i]] = t[i]
                Dt[t[i]] = s[i]

            # Check if the current character is not equal to the 
            # one mapped in the opposite strings dictionary.
            
            # If one condition returns false, then the constraint is broken
            elif s[i] != Dt.get(t[i]) and t[i] != Ds.get(s[i]):
                return False
            
        return True
```