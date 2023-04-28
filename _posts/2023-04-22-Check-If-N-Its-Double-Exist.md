---
title: Check If N and Its Double Exist
date: 2023-04-22 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, hash table]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/check-if-n-and-its-double-exist/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
After a quite strange original solution, I came up with the most optimal solution.

**What Went Wrong**  
Initially, I attempted to implement the optimal solution but was missing an edge case resulting in incorrect answers.

**How I Can Improve**  
I approached the problem as best as possible but didn't spend enough time figuring out why my initial solution wasn't working. 
Once coming back to it after getting a sub-optimal solution to work, I realized it was not that hard of a fix.

**Comments**  
My original solution could be more readable and requires many comments compared to the optimal solution.

# Data Structure Description

Set (hash table) - An unordered collection of distinct elements. Each element may only appear once.

# Optimal Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - We will take n as the list's number of elements. 
We iterate through at most n elements but perform four O(1) operations for each element. 
Since we ignore the O(1) operations, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - We store at most n elements in a set, resulting in the O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
100% of other sumbissions  

# Optimal Solution  

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:
        seen = set()

        for i in arr:

            # If the elements double or half exist in the set
            # then our search criteria are met
            if i*2 in seen or i/2 in seen:
                return True

            # Add the element to the set if they aren't met
            seen.add(i)
            
        return False
```

# Original Solution Statistics  

**Time Spent Coding**  
12 minutes

**Time Complexity**  
O(n * m) - We will take n to be the number of elements in the list and m to be the number of elements in the list of the indices of each element. 
For each element n, we search through their respective list of m elements, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - We will take n to be the number of elements in the list and m to be the number of elements in the list of the indices of each element. 
Since we store a list of m elements for each element, it results in an O(n * m) space complexity.

**Runtime Beats**  
56.16% of other submissions  

**Memory Beats**  
80.79% of other sumbissions  

# Original Solution  

```python
class Solution:
    def checkIfExist(self, arr: List[int]) -> bool:
        nums = {}

        # Fill the nums dictionary with each element
        # and an array of its indicies
        for i,n in enumerate(arr):
            x = nums.get(n,[])
            x.append(i)
            nums[n] = x

        # Iterate through each number in the array
        for i,n in enumerate(arr):

            # If the double of n exists in nums
            if n*2 in nums: 

                # Verifiy the double exists at a different index than i
                for j in nums[n*2]:

                    # If the index is the same, then go to the next index
                    if j == i: continue

                    # If met; return True
                    return True

        return False
```
