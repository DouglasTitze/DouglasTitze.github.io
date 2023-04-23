---
title: Check If N and Its Double Exist
date: 2023-04-22 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [array, hash table, ]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/check-if-n-and-its-double-exist/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I came up with the most optimal solution after a quite strange original solution.

**What Went Wrong**  
Initially I attempted to implement the optimal solution, but was missing an edge case resulting in incorrect answers.

**How I Can Improve**  
I believe I approached the problem as best as I could, but I didn't spend enough time figuring out why my initial solution wasn't working. 
Once coming back to it after getting a sub-optimal solution to work, I realized it was not that hard of a fix.

**Comments**  
My original solution is not very readable and requires a lot of comments compared to the optimal solution.

# Data Structure Description

Set (hash table) - An unordered collection of distinct elements. Each element may only appear once.

# Optimal Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - We will take n to be the number of elements in the list. 
We iterate through at most n elements, but perform four O(1) opertaions each element. 
Since we ignore the O(1) operations, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - We store at most n elements in a set, resulting in the O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
100% of other sumbissions  

# Original Solution  

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:
        seen = set()

        for i in arr:
            if i*2 in seen or i/2 in seen:
                return True
            seen.add(i)
            
        return False
```

# Original Solution Statistics  

**Time Spent Coding**  
12 minutes

**Time Complexity**  
O(n * m) - We will take n to be the number of elements in the list and m to be the number of elements in the list of the indicies of each element. 
For each element n we search through their respective list of m elements, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - We will take n to be the number of elements in the list and m to be the number of elements in the list of the indicies of each element. 
Since we are sotring a list of m elements for each element it results in a O(n * m) space complexity.

**Runtime Beats**  
56.16% of other submissions  

**Memory Beats**  
80.79% of other sumbissions  

# Original Solution  

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:
        nums = {}

        for i,n in enumerate(arr):
            x = nums.get(n,[])
            x.append(i)
            nums[n] = x

        for i,n in enumerate(arr):
            if n*2 in nums: 
                for j in nums[n*2]:
                    if j == i: continue
                    return True

        return False
```
