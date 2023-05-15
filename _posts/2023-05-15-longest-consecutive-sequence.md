---
title: Longest Consecutive Sequence
date: 2023-05-15 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash table, union find]
---


### View *Longest Consecutive Sequence* on [LeetCode](https://leetcode.com/problems/longest-consecutive-sequence/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n) - Each element is visited at most three times, resulting in the O(n) time complexity.  
Although the time complexity should be O(3 * n), big O notation only identifies the rate of increase of the time complexity.

**Space Complexity**  
O(1) - We replace the input list with its set equivalent and do not create any new variables which depend on the list's length, resulting in the O(1) space complexity.

**Runtime Beats**  
50.55% of other submissions  

**Memory Beats**  
50.73% of other sumbissions  

## Explanation
We begin by replacing the `nums` list with its set equivalent to remove duplicates and allow for O(1) lookup time.

We then iterate through each element in the set.  

Within this for loop we will check if a number has an element one less than itself (`n-1 not in nums`).  

- If such an element exists, we continue to the next element. 
This is because this number is not the beginning element of the sequence, and we will eventually encounter it/already have.  

If no such element exists, we have possibly found the beginning of a sequence.  

We will increment that number by one until there are no more elements in its sequence and then check that length against our current longest sequence.

We will return the longest sequence once we iterate through all the elements.


## Solution  

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        longest = 0
        nums = set(nums)

        for n in nums:
            if n-1 not in nums:
                length = 1

                while n+length in nums:
                    length += 1

                longest = max(longest, length)
        
        return longest
```