---
title: Group Anagrams
date: 2023-05-11 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, hash map]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/group-anagrams/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew that all anagrams contain the same characters, so I implemented an approach using this attribute.  
I sorted each word, and using the sorted characters of that word allowed me to have a key that would access all anagrams.

# Data Structure Description

**Hash Map (Dictionary) -** A data structure that stores a collection of keys, each to their respective values. 
Each key may only appear once. 

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n * k) - The number of strings in `strs` is n, and the largest string in `strs` is of length k. 
Assuming the previous values of n and k, we must iterate through all strings in `strs` and each character in each of the strings in `strs`, resulting in the O(n * k) time complexity.
Technically we are iterating through each stings characters twice, but since big O "ignores" constant multiples, the time complexity does not change.

**Space Complexity**  
O(n) - We will never store more values or keys in the dictionary than elements in the `strs` list, resulting in the O(n) space complexity.

**Runtime Beats**  
86.24% of other submissions  

**Memory Beats**  
97.57% of other sumbissions  

# Solution  

```python
class Solution(object):
    def groupAnagrams(self, strs):
        dic = {}

        for s in strs:
            cur = "".join(sorted(s))

            if cur in dic:
                dic[cur].append(s)
            else:
                dic[cur] = [s]
                
        return dic.values()
```
