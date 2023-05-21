---
title: Arranging Coins
date: 2023-05-21 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math, binary search]
---


### View *Arranging Coins* on [LeetCode](https://leetcode.com/problems/arranging-coins/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n log n) - The binary search algorithm takes O(n log n) time resulting in the O(n log n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

## Explanation
Before beginning our binary search, we must initialize our left and right variables with `left, right = 0, n`.

Once initialized, we will continue our search until our left variable exceeds our right or our first conditional statement is met.

We will declare and initialize `mid` inside the loop as the middle integer between the `left` and `right` variables. 
Then, we will calculate the appropriate series sum `sum_s` using the formula `mid * (mid + 1) // 2`. 
With these two variables declared, we can check if the sum is:

*   Equal to `n` (`sum_s == n`), return the midpoint as it is the total number of completed rows
*   Greater than or equal to `n` (`sum_s >= n`), we will assign `right` to the `mid` as binary search requires and increment it by one to avoid repeating the same mid value.
*   Else (if `sum_s` is less than `n`), we will assign `left` to the `mid` as binary search requires and decrement it by one to avoid repeating the same mid value.

If our left variable exceeds our right, we know that our mid value's series sum `sum_s` has not achieved a perfect staircase, so our right value represents the appropriate number of completed rows.

# Algorithm Description

**Binary Search Algorithm -** A sorting algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def arrangeCoins(self, n: int) -> int:
        left, right = 0, n

        while left <= right:
            mid = (right + left) // 2

            sum_s = mid * (mid + 1) // 2
            if sum_s == n:  return mid
            if sum_s >= n:  right = mid - 1
            else:           left = mid + 1

        return right
```