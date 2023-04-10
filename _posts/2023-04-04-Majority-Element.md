---
title: Majority Element
date: 2023-04-04 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, hash table, sorting, counting]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/majority-element/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I solved the question quickly and created a more optimal solution, all in under 10 minutes.

**What I Learned**  
I learned unique one-line solutions by looking at a submission on LeetCode. I recommend looking at them too, [click](https://leetcode.com/problems/majority-element/solutions/3226984/5-different-one-liners-in-python-counter-mode-sort-numpy-and-set/){:target="_blank"} to view.  

**Comments**  
Using the guidance of LeetCode's provided "Follow-up, " it gave me a starting point for how I would approach the optimization.
This is similar to an interviewer asking you to optimize your code, which is a nice addition. 
Looking at old submissions from even two months ago is pleasant because I have come a long way in my coding skills and my general approach to problems.

# Data Structure Description

**Set -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

# Solution Statistics For The Optimal Solution

**Time Spent Optimizing**  
5 Minutes

**Time Complexity**  
O(n) - The program visits each element once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only two new variables are created. 
The number of variables declared does not depend on the number of elements in the array, resulting in the O(1) space complexity. 

**Runtime Beats**  
82.70% of other submissions  

**Memory Beats**  
99.20% of other sumbissions  

# Optimal Solution  

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        maj_elm = ''
        maj_count = 0
        
        for n in nums:
            if maj_count <= 0:
                maj_elm = n
                maj_count = 1
            else:
                if maj_elm == n:
                    maj_count += 1
                else:
                    maj_count -= 1

        return maj_elm
```

# Solution Statistics For The Original Solution

**Time Spent Coding**  
2 Minutes

**Time Complexity**  
O(n) - The program visits each element once, O(n), to copy them into the set and then visits each element in the set, O(n), in the worst case.
Since we choose the largest of the two, it results in an O(n) time complexity.

**Space Complexity**  
O(n) - Since we convert the array into a set, we will have at most n/2 - 1 elements, resulting in the O(n) space complexity.
As n approaches infinity, the division by two has a smaller and smaller effect on the result, making it irrelevant to the space complexity.

**Runtime Beats**  
91.57% of other submissions  

**Memory Beats**  
75.52% of other sumbissions  

# Solution  

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        for n in set(nums):
            if nums.count(n) > len(nums)/2:
                return n
```
