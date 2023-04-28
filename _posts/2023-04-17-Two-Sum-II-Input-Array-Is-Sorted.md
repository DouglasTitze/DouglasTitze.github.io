---
title: Two Sum II - Input Array Is Sorted
date: 2023-04-17 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, two pointers, binary search]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew to use the two-pointer method because the list was sorted.

**What I Learned**  
I further solidified the two-pointer method in my brain.

# Algorithm Description

**Two Pointer Algorithm -** If a list is sorted and we place a pointer at the extreme values (max and min), we can iterate one pointer at a time to approach the solution.

**Visual Examples**  
The two-pointer algorithm being performed on a list, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - In the worst case, the target indices are near the middle, resulting in the O(n) time complexity because almost all indices will be visited.

**Space Complexity**  
O(1) - We only need to declare two new variables, and the number of variables does not depend on the number of elements in the list (n), resulting in the O(1) space complexity.

**Runtime Beats**  
79.62% of other submissions  

**Memory Beats**  
80.90% of other sumbissions  

# Solution  

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        p0 = 0
        p1 = len(numbers) - 1

        while p1 > p0:
            # If the elements at the indices sum to the target
            if numbers[p0] + numbers[p1] == target:
                # Return them, but add one 
                # (This is a special constraint that only applies to this problem)
                return [p0+1,p1+1]

            # If the number is greater than the target, then we know if we decrement
            # p1 we will get a smaller value, there for inching closer to the target
            if numbers[p0] + numbers[p1] > target:
                p1 -=1

            # The same principle applies here, except the sum is smaller than the target
            # and incrementing p0 gets us a larger value
            else:
                p0 +=1
```
