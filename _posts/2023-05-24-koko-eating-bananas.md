---
title: Koko Eating Bananas
date: 2023-05-24 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search]
---


### View *Koko Eating Bananas* on [LeetCode](https://leetcode.com/problems/koko-eating-bananas/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(log (max(piles)) * n) - We perform binary search on the interval 1 to `max(piles),` and for each search, we perform an operation that iterates through every element in `piles` (n), resulting in the O(log (max(piles)) * n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

**Runtime Beats**  
99.56% of other submissions  

**Memory Beats**  
15.24% of other sumbissions  

## Explanation
Before performing a binary search, we must initialize our left and right variables; in this problem, we will never have a result that is less than one or greater than the largest number in the list; for that reason, we assign these values to our variables.

We will start and continue the `while` loop until `l` is larger than `r.` Inside the loop, we initialize `m` to the middle of `l` and `r` and our time variable `t` to 0.

We then execute `for p in piles: t += ceil(p/m)`, which calculates and stores Koko's total time to eat all the bananas.

*   If `t` is larger than `h`, Koko must eat faster, so we move the `l` to `m + 1`.
*   If `t` is not larger than `h`, then Koko may be able to eat slower, so we move the `r` to `m - 1`.

Once our `while` loop conditional is broken, the minimum speed Koko can eat is stored in `l`; since we are only incrementing `l` if the time it takes to eat all the bananas is larger than `h,` `l` is not affected by the last iteration of the `while` loop, therefore leaving the correct answer in `l.`


**Side Note**: While I do not know why, to find the result faster, you can initialize `l` and `r` using the following code.
```python
Sum = sum(piles)
l = ceil(Sum/h)
r = ceil(Sum/(h-len(piles)+1))
```

## Algorithm Description

**Binary Search Algorithm -** A sorting algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def minEatingSpeed(self, piles: List[int], h: int) -> int:
        l = 1
        r = max(piles)

        while l <= r:
            m = (l+r)//2
            t = 0

            for p in piles: t += ceil(p/m)

            if t > h: l = m+1
            else:     r = m-1

        return l
```