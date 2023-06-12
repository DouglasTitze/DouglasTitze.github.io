---
title: Length of Longest Fibonacci Subsequence
date: 2023-06-11 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash table, dynamic programming]
---

### View *Length of Longest Fibonacci Subsequence* on [LeetCode](https://leetcode.com/problems/length-of-longest-fibonacci-subsequence/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
30 minutes

**Time Complexity**  
O(n<sup>2</sup>log m) - The n<sup>2</sup> comes from the nested for loop, where `n` is the length of `arr,` and the `log m` comes from the `while` loop, where `m` is the maximum integer in `arr.`

**Space Complexity**  
O(n) - The elements in `arr` are duplicated and placed into a set, resulting in the O(n) space complexity.

**Runtime Beats**  
33% of other submissions  

**Memory Beats**  
79.50% of other sumbissions  

## Explanation  
Before iterating through the list, initialize the set `s` to allow for O(1) lookup time for the Fibonacci numbers and a result `res` variable to hold the longest result.

Begin iterating `i` through 0 -> len(arr)-2, and inside of that, iterate `j` through i+1 -> len(arr).

Once inside the nested for loop, declare and initialize `x1` to the second element in the Fibonacci sequence and `x2` to the third element (e.g., 1 2 3  -> x1 = 2, x2 = 3); this is to avoid a redundant iteration of the while loop since the while loop will verify if the third element is in the set. Also, declare and initialize `count` to 2 since it is known that arr[i] and arr[j] are within the input list `arr.`

`While` the value of x2 is within the set, increase the Fibonacci sequence by re-assign `x1` to `x2` and `x2` to the sum of itself and `x1` and increment the count variable.

When the `while` loop exists, assign the maximum between res and the count.

Finally, when both for loops terminate, if the result is less than 3, there were no valid Fibonacci subsequences, and 0 must be returned.
Otherwise, return the result.


## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  


## Solution  

```python
class Solution:
    def lenLongestFibSubseq(self, arr: List[int]) -> int:
        s = set(arr)
        res = 0

        for i in range(len(arr)-2):
            for j in range(i+1,len(arr)):
                x1 = arr[j]
                x2 = arr[j] + arr[i]
                count = 2

                while x2 in s:
                    x1,x2 = x2, x2 + x1
                    count +=1

                res = max(res,count)

        if res < 3: return 0

        return res
```