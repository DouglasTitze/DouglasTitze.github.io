---
title: Maximum Subarray
date: 2023-03-26 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, dynamic programming]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/maximum-subarray/description/){:target="\_blank"} on LeetCode

# My Thoughts

**What Went Well**  
Since I had previously worked on this question before, I was able to solve it in just two minutes.

**What I Learned**  
I refreshed my memory on the algorithm's name, although I recalled how to implement it despite not knowing its name.

**Comments**  
I was able to solve this question so quickly because I struggled with it a lot in the past. 
The first time I encountered this question, I was so frustrated that I could not figure it out because it seemed like an easy task. 
To better understand the algorithm, I watched a tutorial and found that the visual representation solidified this algorithm in my brain.

# Algorithm Description

**Kadane's Algorithm -** An iterative dynamic programming algorithm often used to find the maximum subarray. 
The algorithm tracks the local/current sum and the global sum. It iterates through the array and updates these values with the largest. 
Local/current sum either updates to the current array value or the current sum plus that value. 
Global sum either updates to the global sum or the current sum.

**Visual Examples**  
Kadane's Algorithm being performed on an array, [click](https://storage.googleapis.com/algodailyrandomassets/curriculum/dynamic-programming/kadence-dry-run.png){:target="\_blank"} to view 

# Solution Statistics

**Time Spent Coding**  
2 Minutes

**Time Complexity**  
O(n) - Each element in the array is only visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only two new variables are created.
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.

**Runtime Beats**  
47.76% of other submissions

**Memory Beats**  
96.85% of other sumbissions

# Solution

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # We must initialize to either -infinity or the first value in the array
        # To make the for loop more understandable, I chose -infinity
        curMax = globalMax = -inf

        for n in nums:
            curMax = max(n,curMax+n)
            globalMax = max(globalMax,curMax)

        return globalMax
```
