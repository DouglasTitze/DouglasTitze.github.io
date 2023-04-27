---
title: Product of Array Except Self
date: 2023-04-25 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [dynamic programming, prefix sum]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/product-of-array-except-self/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew I had to utilize dynamic programming and maintain a list or variable of the left and right products.

**What Went Wrong**  
Implementing left and right products was much more difficult than I thought.  I kept thinking of ways that used division, which this problem did not permit.

**What I Learned**  
I learned a few different ways to solve this problem, and they each uniquely approached implementing dynamic programming.

**How I Can Improve**  
Dynamic programming has proven itself to be a difficult concept to grasp, but all I can keep doing is studying. 
Analyzing other solutions to recognize patterns in their approaches and watching youtube videos is what I am currently doing.

**Comments**  
I am getting better at recognizing when dynamic programming is needed, but knowing exactly how to is still challenging since it is a very generalized term.

**Visual Examples of The Solution**  
[Example 1, click](https://drive.google.com/file/d/14IM4ou9bmGdiBdr1Ez3pXP_OmIKs1T7o/view?usp=sharing){:target="_blank"} to view  
[Example 2, click](https://drive.google.com/file/d/1VYgoAlu3FvNRsYxwaFXea8jKoQK5Dkx2/view?usp=share_link){:target="_blank"} to view  
[Example 3, click](https://drive.google.com/file/d/1aA9I08cEIGjc8v3fx0MeUdfnBjbu_gaq/view?usp=share_link){:target="_blank"} to view  

# Solution Statistics  

**Time Complexity**  
O(n) - We iterate through the input array nums twice, resulting in O(n*2), but big O ignores constant multiples, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - This problem states that the output array does not contribute to the space complexity, resulting in the O(1) space complexity.  
If this were not the case, our space complexity would be O(n) since we create an array with the same number of elements as the input array.

**Runtime Beats**  
97.5% of other submissions  

**Memory Beats**  
88.61% of other sumbissions  

# Solution  

```python
class Solution:
    def productExceptSelf(self, nums):
        # Create an array that will hold the result
        # and has the same number of elements as nums
        dp = [1] * len(nums)

        # Alter dp so dp[i] = left product
        # Left prod = the product of all elements to the left of i
        prod = 1
        for i in range(len(nums)):
            dp[i] = prod
            prod *= nums[i]

        
        # Since dp[i] is storing the left product, this loop alters the
        # array so each element represents left prod * right prod
        
        # Alter dp so dp[i] = dp[i] * right prod
        # Right prod = the product of all elements to the right of i
        prod = 1
        for i in range(len(nums)-1,-1,-1):
            dp[i] *= prod
            prod *= nums[i]

        return dp
```