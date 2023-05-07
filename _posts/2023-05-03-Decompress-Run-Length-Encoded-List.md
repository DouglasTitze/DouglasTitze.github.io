---
title: Decompress Run-Length Encoded List
date: 2023-05-03 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/decompress-run-length-encoded-list/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I solved the problem quickly and learned unique ways to solve this problem using operations I had never seen before. 
I also learned about the run-length encoding algorithm.

# Solution Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n * k) - We are taking n as the number of elements in the input list and k as the number of elements in the list being appended to ```ret```. The extend function iterates through the list being appended to the ```ret``` list, resulting in the O(n * k) time complexity since this occurs in each loop.

**Space Complexity**  
O(n * k) - We store each 2nd element from the input list k times in the ```ret``` list, resulting in the O(n * k) space complexity.

**Runtime Beats**  
73.79% of other submissions  

**Memory Beats**  
96.37% of other sumbissions  

# Solution  

```python
class Solution(object):
    def decompressRLElist(self, nums):
        ret = []

        # Each iteration, we are accessing two elements, we must
        # increment through the list by two elements at a time
        for i in range(0,len(nums),2):
            # val = nums[i+1]
            # frquency = nums[i]
            ret.extend([nums[i+1]]*nums[i])

        return ret
```
