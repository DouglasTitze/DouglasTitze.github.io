---
title: Monotonic Array
date: 2023-07-10 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array]
---

### View *Monotonic Array* on [LeetCode](https://leetcode.com/problems/monotonic-array/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n log n) - In the worst case, the input array is not sorted, and the sort method must sort the array, resulting in an O(n log n) time complexity.

**Space Complexity**  
O(n) - The elements from the input list must be stored in the `sort` variable, resulting in the O(n) space complexity.

**Runtime Beats**  
69.87% of other submissions  

**Memory Beats**  
78.23% of other sumbissions  

## Explanation  
A monotonic array is an array that is always increasing/decreasing or constant.

To verify if an array is monotonic, sort the input array and check if the input array equals the sorted array or the reverse of the sorted array.

```python
class Solution:
    def isMonotonic(self, nums: List[int]) -> bool:
        sort = sorted(nums)
        if nums == sort or nums == sort[::-1]:
            return True
            
        return False
```