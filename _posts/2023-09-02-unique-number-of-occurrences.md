---
title: Unique Number of Occurrences
date: 2023-09-02 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash table, hash map]
---

### View *Unique Number of Occurrences* on [LeetCode](https://leetcode.com/problems/unique-number-of-occurrences/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - In the worst case, every element in the input list will be visited twice, but constant multiples of n do not increase the growth rate, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst case, every element in the input list will be stored twice, but constant multiples of n do not increase the growth rate, resulting in the O(n) space complexity.

**Runtime Beats**  
99.39% of other submissions    

## Explanation  
_The comments explain the program._

## Data Structures Used  

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view


## Solution  

```python
class Solution:
    def uniqueOccurrences(self, arr: List[int]) -> bool:

        # Create and fill a dictionary of each number and their frequencies
        count_of = defaultdict(int)
        for num in arr:
            count_of[num] += 1

        # Create and fill a set with each frequency from the dictionary
        freqs = set()
        for freq in count_of.values():
            # If the frequency is not already in the set, then add it
            if freq not in freqs:
                freqs.add(freq)

            # If it is in the set, then the input array is invalid; return False
            else:
                return False

        return True
```