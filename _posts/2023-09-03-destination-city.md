---
title: Destination City
date: 2023-09-03 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table, array]
---

### View *Destination City* on [LeetCode](https://leetcode.com/problems/destination-city/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - In the worst case, every element in the input list will be visited twice, but constant multiples of n do not increase the growth rate, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst case, every element in the input list will be stored twice, but constant multiples of n do not increase the growth rate, resulting in the O(n) space complexity.

**Runtime Beats**  
99.93% of other submissions  

**Memory Beats**  
89.62% of other sumbissions  

## Explanation  
_The comments explain the program._

## Data Structures Used  

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view

## Solution  

```python
class Solution:
    def destCity(self, paths: List[List[str]]) -> str:
        # Initialize sets to store all starting and ending cities
        startings = set()
        endings = set()
        
        # Fill sets with corresponding elements from the input list
        for s, e in paths:
            startings.add(s)
            endings.add(e)

        # Iterate through all ending cities, until one is not found within the starting citites set
        for e in endings:
            if e not in startings:
                return e
```