---
title: Number of Arithmetic Triplets
date: 2023-06-19 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table]
---

### View *Number of Arithmetic Triplets* on [LeetCode](https://leetcode.com/problems/number-of-arithmetic-triplets/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - Every number in the input list is iterated over, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Every number in the input list is duplicated and stored in a set, resulting in the O(n) space complexity.

**Runtime Beats**  
83.12% of other submissions  

**Memory Beats**  
61.69% of other sumbissions  

## Explanation  
Before iterating through the input list, create a variable to track every triplet, and to reduce time complexity, convert the input list into a set.

Begin iterating over each number `n` in nums, and check if `n - diff and n - diff*2` are in the set:
*   If true, `n` has a triplet
*   If false, continue to the following number

_All triplets follow the if statements logic_

Once the for loop is complete, `return num_triplets`


## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

## Solution  

```python
class Solution:
    def arithmeticTriplets(self, nums: List[int], diff: int) -> int:
        seen = set(nums)
        num_triplets = 0

        for n in nums:
            if n - diff in seen and n - diff*2 in seen:
                num_triplets +=1
        return num_triplets
```