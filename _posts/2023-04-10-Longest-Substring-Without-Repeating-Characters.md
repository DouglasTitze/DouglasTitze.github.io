---
title: Longest Substring Without Repeating Characters
date: 2023-04-10 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [hash table, string, sliding window]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/longest-substring-without-repeating-characters/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I found a solution quickly and had a runtime similar to the optimal solution.

**What Went Wrong**  
I was unable to find the optimal solution or optimize my code. 
When implementing a dictionary into my solution to remove a nested O(n) operation, it ended up doubling my runtime despite "reducing" my time complexity to O(n).

**What I Learned**  
I brushed up on the sliding window technique and how the algorithm works in various scenarios.
The input must be more significant than 50,000 characters (the longest tested string) to substantially change the optimized solution's runtime.

**How I Can Improve**  
Although I recognized the algorithm which needed to be used, I could not figure out how to implement it, which is why I came up with the solution I did.

**Comments**  
All the solutions which use the sliding window technique received much worse runtimes and memory statistics.
I wonder if this is an issue with the data used to test the solutions or if dictionary mutations affect the runtime by that large of a margin.

# Algorithm Description

**Sliding Window Technique -** An algorithm that takes in a subset of data from an iterable object and expands or reduces that subset based on given conditions.

This problem would expand the subset when a unique character is found and reduce it when a duplicate is found.

**Visual Examples**  
An intense dive into the sliding window technique can be found here, [click](https://www.youtube.com/watch?v=jM2dhDPYMQM){:target="_blank"} to view  
Unfortunately, all the other resources I found that spoke about the sliding window technique covered only some of its use cases.

# Solution Statistics  

**Time Spent Coding**  
9 minutes

**Time Complexity**  
O(n<sup>2</sup>) - For each character in s that does not repeat, we will append it to an array and then iterate through that array. Both of these operations are O(n), and since the second is nested within the first O(n) operation, it results in an O(n<sup>2</sup>) time complexity.

**Space Complexity**  
O(n) - If the input string does not contain duplicates, we will replicate the string, resulting in the O(n) space complexity.

**Runtime Beats**  
83.80% of other submissions  

**Memory Beats**  
87.34% of other sumbissions  

# Solution  

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        sub = []   # O(1)
        len_sub = 0   # O(1)

        for char in s:   # O(n)

            # If the character is in the substring array, then remove all
            # elements in the array from the index 0 until the duplicate, inclusive
            if char in sub:   # O(n)
                len_sub = max(len(sub),len_sub)   # O(1)
                sub = sub[sub.index(c)+1:]   # O(n)
                sub.append(c)   # O(1)

            else:
                sub.append(c)   # O(1)

        return max(len(sub),len_sub)   # O(1)
```