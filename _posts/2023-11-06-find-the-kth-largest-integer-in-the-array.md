---
title: Find the Kth Largest Integer in the Array
date: 2023-11-06 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, sorting]
---

### View *Find the Kth Largest Integer in the Array* on [LeetCode](https://leetcode.com/problems/find-the-kth-largest-integer-in-the-array/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n log n), The input array must be sorted, resulting in the O(n log n) time complexity.

**Space Complexity**  
O(n) - The intermediary space that is required to sort the array is O(n).

**Runtime Beats**  
99.67% of other submissions  

**Memory Beats**  
94.99% of other sumbissions  

## Explanation  
The map object tells Python when it iterates over an element in the nums list to convert it into an integer before operating on it. This allows the program to convert each element in nums to an integer while it is being sorted, therefore slightly reducing the time complexity (reduces time complexity by n, but O(n log n) is still a more significant growth rate than n, so the time complexity technically does not change.

Once nums is sorted, get the kth element (k-1 since 0 indexed).

## Solution  

```python
class Solution:
    def kthLargestNumber(self, nums: List[str], k: int) -> str:
        # Create a map object
        str_to_int = map(int, nums)

        # Sort and return a list of the map object
        nums = sorted(str_to_int, reverse=True)

        # Return the kth element in its original format (string)
        return str(nums[k-1])
```