---
title: Concatenation of Array
date: 2023-04-29 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [array]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/concatenation-of-array/){:target="_blank"} on LeetCode  

# My Thoughts  

**What I Learned**  
I refreshed my memory on a list method I had not used in a long time.

**Comments**  
I forgot this method existed since I do not typically want arrays to concatenate.

# Solution Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n) - We must iterate through each element in the array (O(n)) and append it (O(1)) to the array, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - We store each array element twice, resulting in an O(n * 2) space complexity. 
Since big O ignores constant multiples of n, the true space complexity is O(n).  

One could argue that the problem asks us to store each element twice, meaning the problem does not want you to count the output array in the time complexity, but that is usually specified.

**Runtime Beats**  
99.33% of other submissions  

**Memory Beats**  
16.12% of other sumbissions  

# Solution  

```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        nums.extend(nums)
        return nums
```
