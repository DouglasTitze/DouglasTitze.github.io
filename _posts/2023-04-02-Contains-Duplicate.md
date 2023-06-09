---
title: Contains Duplicate
date: 2023-04-02 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table, hash map, sorting, array]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/contains-duplicate/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I remembered sets and their properties.

**What I Learned**  
I learned how to solve this problem using javascript to remove some rust. 
I also learned how to create a visual for this problem since I couldn't find one online.

**Comments**  
Due to how much syntactic sugar python has, this was the fastest I've ever, and will ever, complete a question. 

Another approach to this problem could be the use of a hash table or dictionary. 
You can iterate through the nums array and add elements into the dictionary until you encounter an element already inside the dictionary. This approach is viable because of dictionaries' O(1) access time.

# Data Structure Description

**Hash Table (Set) -** An unordered container of non-repeating values.  
**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

Illustration of key value pair mapping, [click](https://www.learnbyexample.org/wp-content/uploads/python/Dictionary-Key-Value-Pairs-Illustration.png){:target="_blank"} to view   

# Solution Statistics  

**Time Spent Coding**  
50 Seconds

**Time Complexity**  
O(n) - All the array elements must be duplicated and counted. All the elements in the set must also be counted. 
These operations are O(n), resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - If the array does not contain duplicates, the set will have n elements, resulting in the O(n) space complexity. 

**Runtime Beats**  
88.26% of other submissions  

**Memory Beats**  
79.5% of other sumbissions  

# Solution  

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # ***Explanation of the oneliner***
        #
        # s = set(nums)
        #
        # Since a set can not contain duplicates if the lengths are not equal
        # then the nums array must contain duplicates
        # if len(nums) != len(s):
        #   return False
        #
        # else:
        #   return True

        return len(nums) != len(set(nums))
```
