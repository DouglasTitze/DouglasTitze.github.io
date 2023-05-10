---
title: Create Target Array in the Given Order
date: 2023-05-09 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/create-target-array-in-the-given-order/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I came up with two different approaches to the problem using techniques I learned about this year, so I am glad I got some practice with them.

# Algorithm Description

**Zip (built-in function) -** Returns a zip object generator, which contains pairs of the index i's of each input list up to the length of the shortest list.

**Visual Examples**  
Zip in action, [click](https://blog.finxter.com/wp-content/uploads/2021/01/zip-768x432.jpg){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
3 minutes

**Time Complexity**  
O(n) - We must iterate through each element in index/nums lists and again to add their elements to the return list, but the zip generator access each element at access time, meaning we only iterate through each list once, resulting in the O(n) time complexity. 
If the zip operator did not do this, the time complexity would be O(2 * n), which would still reduce to O(n).

**Space Complexity**  
O(n) - We must store a return list containing each element in the nums list, resulting in the O(n) space complexity since both the nums and index list have the same number of elements.

**Runtime Beats**  
88.65% of other submissions  

**Memory Beats**  
87.23% of other sumbissions  

# Solution  

```python
class Solution(object):
    def createTargetArray(self, nums, index):        
        ret = []
        
        for i,n in zip(index,nums):
            ret.insert(i,n)
            
        return ret

        # ret = []
        # for i, insert_index in enumerate(index):
        #     ret.insert(insert_index, nums[i])
        # return ret
```
