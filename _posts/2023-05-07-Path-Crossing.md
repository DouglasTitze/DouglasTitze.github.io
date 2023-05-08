---
title: Path Crossing
date: 2023-05-07 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string, hash table]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/path-crossing/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew how to use a set and convert each path into its 2D representation.

# Data Structure Description

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Each element in the ```path``` list must be visited once, and each of ```path```'s elements only performs O(1) operations, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each tuple (coordinate) must be stored for each element in the ```path``` list, resulting in the O(n) space complexity. 

**Runtime Beats**  
87.14% of other submissions  

**Memory Beats**  
98.57% of other sumbissions  

# Solution  

```python
class Solution(object):
    def isPathCrossing(self, path):
        x = y = 0
        visited = set()
        visited.add((0,0))

        for p in path:
            if p == "N":   y +=1
            elif p == "S": y -=1
            elif p == "E": x +=1
            else:          x -=1

            if (x,y) in visited: 
                return True
            else:               
                visited.add((x,y))

        return False

```
