---
title: Left and Right Sum Differences
date: 2023-04-21 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, prefix sum]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/left-and-right-sum-differences/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I solved the question with very space-conscious answers and improved my time complexity by a substantial amount.

**Comments**  
I thought my first solution would be more space efficient, but that was incorrect after creating the optimized solution.

# Optimal Solution Statistics  

**Time Spent Optimizing**  
4 minutes

**Time Complexity**  
O(n) - We must iterate through each element in the list once, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - We must return an array of results with a length equivalent to n, resulting in the O(n) space complexity.

**Runtime Beats**  
90.77% of other submissions  

**Memory Beats**  
92.00% of other sumbissions  

# Optimal Solution  

```python
class Solution:
    def leftRigthDifference(self, nums: List[int]) -> List[int]:
        # Eliminate the edge case of only one element
        if len(nums) == 1: return [0]

        # Create the answer array with n elements; all 0's
        ans = [0]*len(nums)

        # Initialize the left and right sums
        lsum = 0
        rsum = sum(nums[1:])

        for i in range(len(nums)-1):

            # Calculate the absolute value and store it at i
            ans[i] = abs(lsum - rsum)

            # Decrement/increment l/rsums
            lsum += nums[i]
            rsum -= nums[i+1]

        # Because we are only iterating through n-1 elements
        # we would miss the last index of the answer array
        # without this line
        ans[-1] = lsum

        return ans
```

# Original Solution Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n<sup>2</sup>) - We iterate through each element in the list, and for each element, we iterate through the n-1 elements.
Since 1 is a constant, we ignore it, and are left with an O(n) loop within an O(n) loop, resulting in the O(n<sup>2</sup>) time complexity.

**Space Complexity**  
O(n) - We must return an array of results with a length equivalent to n, resulting in the O(n) space complexity.

**Runtime Beats**  
15.88% of other submissions  

**Memory Beats**  
92.00% of other sumbissions  

# Original Solution  

```python
class Solution:
    def leftRigthDifference(self, nums: List[int]) -> List[int]:
        # Create the answer array with n elements; all 0's
        ans = [0]*len(nums)

        for i,num in enumerate(nums):

            # Set the current answer index to the left sum
            ans[i] = sum(nums[0:i])
            
            # If the right sum will have one or more elements, then calculate
            # the absolute value and store it back at the same index
            if i+1 <= len(nums):
                ans[i] = abs(ans[i] - sum(nums[i+1:]))

        return ans
```
