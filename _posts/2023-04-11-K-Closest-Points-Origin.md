---
title: K Closest Points to Origin
date: 2023-04-11 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [array, math, sorting]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/k-closest-points-to-origin/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I recently learned about the "key = " sorting feature and applied it to this problem to solve the question almost instantly.

# Solution Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n log n) - The built-in sort method takes O(n log n) time, resulting in the O(n log n) space complexity.  

O(n log n) is the fastest possible runtime for sorting algorithms.

**Space Complexity**  
O(1) - The built-in sort method sorts the list in place, resulting in the O(1) space complexity.

**Runtime Beats**  
99.99% of other submissions  

**Memory Beats**  
99.99% of other sumbissions  

# Solution  

```python
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        # The sort function sorts each element of the list based off their
        # squared sums (x^2 + y^2)
        points.sort(key = lambda x: x[0]**2 + x[1]**2)

        # We then return from 0 to k elements of the sorted list
        return points[:k]
```
