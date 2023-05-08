---
title: Strong Password Checker II
date: 2023-05-08 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string, hash table, hash map]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/strong-password-checker-ii/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew how to approach the problem optimally, and I had fun while doing so because I got to combine a lot of different data structures and operations.

**Comments**
We could optimize the code further by checking the first element outside of the ```for loop```, so then we would only need to check if c2 meets the criteria, but this would add a lot of confusion and lines to the program. 
Furthermore, since the password's maximum length is only 100 characters, the potential speedup for this improvement will not be seen.

# Data Structure Description

**Hash Map (Dictionary) -** A data structure that stores a collection of keys, each to their respective values. 
Each key may only appear once. 

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
6 minutes

**Time Complexity**  
O(n) - Each character in the password must be seen at least once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the length of the password, resulting in the O(1) space complexity.

**Runtime Beats**  
96.50% of other submissions  

**Memory Beats**  
68.42% of other sumbissions  

# Solution  

```python
class Solution(object):
    def strongPasswordCheckerII(self, password):
        if len(password) < 8: return False

        criteria = { "lower" : False,
                     "upper" : False,
                     "digit" : False,
                     "Special" : False
                    }

        specials = set(["!","@","#","$","%","^","&","*","(",")","-","+"])
        for i,c1 in enumerate(password[:len(password)-1]):
            c2 = password[i+1]

            # If character1 (c1) is equal to c2 (its adjacent character)
            # return False, this password is invalid (not strong)
            if c1 == c2: return False

            if c1.isupper() or c2.isupper():
                criteria["upper"] = True
            
            if c1.islower() or c2.islower():
                criteria["lower"] = True
            
            if c1.isdigit() or c2.isdigit():
                criteria["digit"] = True
            
            if c1 in specials or c2 in specials:
                criteria["special"] = True

        # If the criteria dictionary contains false as one of its values
        # then the password did not meet all criteria, return False
        return False not in criteria.values()
```
