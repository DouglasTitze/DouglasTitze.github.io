---
title: Random Pick Index
date: 2023-11-01 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash table]
---

### View *Random Pick Index* on [LeetCode](https://leetcode.com/problems/random-pick-index/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - The program must initialize the hash table with the user input, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The program must store all of the user's input numbers, resulting in the O(n) space complexity.

**Runtime Beats**  
95.45% of other submissions  

**Memory Beats**  
85.52% of other sumbissions  

## Explanation  
To decrease the time complexity of each call of the method `pick` the program initializes a dictionary of `target : indicie` pairs. This allows for quick access to the indices where `target` only leaivng a random selection of an index, which is an O(1) operation, making `pick` take O(1). 

## Data Structure Used  

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view

## Solution  

```python
import random
class Solution:

    def __init__(self, nums: List[int]):
        self.nums = {}
        
        for i,n in enumerate(nums):
            if n not in self.nums:
                self.nums[n] = [i]
            else:
                self.nums[n].append(i)

    def pick(self, target: int) -> int:
        return random.choice(self.nums[target])
```