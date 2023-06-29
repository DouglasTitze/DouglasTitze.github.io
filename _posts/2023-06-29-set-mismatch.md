---
title: Set Mismatch
date: 2023-06-29 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math, hash table]
---

### View *Set Mismatch* on [LeetCode](https://leetcode.com/problems/set-mismatch/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - The list is iterated through when creating the set, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The computer must have enough memory to temporarily hold the set representation of the list, even if it is only used for under a second, resulting in the O(n) space complexity.

**Runtime Beats**  
97.59% of other submissions  

**Memory Beats**  
56.96% of other sumbissions  

## Explanation  
The program calculates the `correct_sum` of nums using the series sum formula. 
Using the correct result of the nums list allows for a straightforward calculation of the repeating and missing numbers.

Repeated number - `sum(nums) - set_sum`, this calculation returns the repeated number because converting the list to a set eliminates the duplicate making the difference the repeated number.

Missing number - `correct_sum - set_sum`, since the repeated number does not contribute to finding the missing number, `set_sum` is used, making the difference the missing number. 

## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view


## Solution  

```python
class Solution:
    def findErrorNums(self, nums: List[int]) -> List[int]:
        l = len(nums)
        correct_sum = l * (l+1) // 2
        set_sum = sum(set(nums))
        
        return [sum(nums) - set_sum, correct_sum - set_sum]
```