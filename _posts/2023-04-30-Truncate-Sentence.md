---
title: Truncate Sentence
date: 2023-04-30 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, string]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/truncate-sentence/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I have encountered a very similar problem to this one and knew how to solve it instantly.

**Comments**  
All the submissions are identical, so more recent submissions have higher statistics, while later submissions have lower.

# Solution Statistics  

**Time Spent Coding**  
10 seconds

**Time Complexity**  
O(n + k) - We must iterate through each element in s, which has n elements separated by spaces, and then the output array, which will have k elements, resulting in the O(n + k) time complexity.

**Space Complexity**  
O(n) - We must duplicate all elements in s to compute the intermediate array, resulting in the O(n) space complexity. 
All other intermediates are smaller than n, and those intermediates also overwrite n, so they do not "count" towards space complexity since they store less data than n.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
93.72% of other sumbissions  

# Solution  

```python
class Solution:
    def truncateSentence(self, s: str, k: int) -> str:
        # .split() - Creates an array of all elements in s separated by white space
        # [:k] - Extracts the number of elements requested into another array
        # " ".join() - Concatenates the elements in the array, separating each element with a space
        return " ".join(s.split()[:k])
```
