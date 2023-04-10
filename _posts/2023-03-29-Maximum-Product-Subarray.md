---
title: Maximum Product Subarray
date: 2023-03-29 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, dynamic programming]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/maximum-product-subarray/){:target="\_blank"} on LeetCode

# My Thoughts  

**What Went Well**  
My experience with Kadane's algorithm and it sharing similarities with this problem, I solved it quickly.

**What Went Wrong**  
Debugging was slow, but overall I am pleased with the speed I solved this problem.

**What I Learned**  
I learned how to alter Kadane's algorithm to produce the maximum product as the output.

**Comments**  
I was familiar with the approach to solving this problem, but sketching out potential solutions on paper allowed me to find the most efficient solution much faster. 

# Algorithm Description

**Kadane's Algorithm -** An iterative dynamic programming algorithm often used to find the maximum subarray. 
The algorithm tracks the local/current sum and the global sum. It iterates through the array and updates these values with the largest. 
Local/current sum either updates to the current array value or the current sum plus that value. 
Global sum either updates to the global sum or the current sum.  

This iteration of the algorithm tracks the current minimum, current maximum, and global maximum, and instead of the largest sum, it returns the maximum product.

**Visual Examples**  
Kadane's Algorithm being performed on an array, [click](https://storage.googleapis.com/algodailyrandomassets/curriculum/dynamic-programming/kadence-dry-run.png){:target="\_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
7 minutes

**Time Complexity**  
O(n) - Each element in the array is only visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only three new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.

**Runtime Beats**  
72.43% of other submissions  

**Memory Beats**  
98.57% of other sumbissions  

# Solution  

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        # Negative numbers exist in this data set, so we can not use -infinity
        # We must assign the first element to be the starting point for all variables
        curMin = curMax = globalProd = nums[0]

        for n in nums[1:]:
            # To avoid accidentally multiplying by n twice, we must save the previous 
            # curMax in a variable
            saveMax = curMax

            curMax = max(curMax*n,curMin*n,n)
            curMin = min(saveMax*n,curMin*n,n)

            globalProd = max(curMax,curMin,globalProd)

        return globalProd
```
