---
title: Array Partition
date: 2023-05-04 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, sorting]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/array-partition/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I had fun messing around with my solution to reduce its number of lines and find faster solutions.

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n log n) - Sorting the array takes O(n log n), and then we must increment through the sorted array, but since O(n log n) is the greatest time complexity, we are left with an O(n log n) time complexity.

**Space Complexity**  
O(n) - Every second element from the input list must be stored, making the space complexity O(n/2). Still, since dividing n does not change the rate of increase (linear, exponential, etc.), it results in an O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
62.60% of other sumbissions  

# Solution  

```python
class Solution(object):
    def arrayPairSum(self, nums):
        # All of the following solutions sort the input list
        # add the least value of each pair, and repeat this
        # until n (length of nums)

        return sum(sorted(nums)[::2])

        # nums.sort()
        # return sum(nums[::2])

        # s = 0
        # nums.sort()
        # for i in range(0,len(nums),2):
        #     s += nums[i]
        #
        # return s
```
