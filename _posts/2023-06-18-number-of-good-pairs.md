---
title: Number of Good Pairs
date: 2023-06-18 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash map, math, counting]
---

### View *Number of Good Pairs* on [LeetCode](https://leetcode.com/problems/number-of-good-pairs/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n) - Each element in the input list is visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst-case scenario, each number in the input list is unique, requiring the duplication of each element, resulting in an O(n) space complexity.

**Runtime Beats**  
73.43% of other submissions  

**Memory Beats**  
98.97% of other sumbissions  

## Explanation  
Pairs are recorded in the `pairs` dictionary, and `total` is the sum of all the possible pairs.

For each element in nums, check if it is in pairs:
*   If true, add the total number of pairs before the current iteration and then add one.
*   If false, add the element to the pairs dictionary.

The repetition of this if statement replicates the formula to calculate combinations and accurately calculates the number of pairs in the input list.

## Data Structure Used

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

## Solution  

```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        pairs = {}
        total = 0

        for n in nums:
            if n in pairs:
                total += pairs[n]
                pairs[n] += 1
            else:
                pairs[n] = 1

        return total

```