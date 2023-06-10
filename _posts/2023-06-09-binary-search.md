---
title: Binary Search
date: 2023-06-09 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, binary search]
---

### View *Binary Search* on [LeetCode](https://leetcode.com/problems/binary-search/description/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(log n) - The binary search algorithm takes at most O(log n) time.

**Space Complexity**  
O(1) - The number of variables created is independent of the input list, resulting in the O(1) space complexity.

## Explanation
To set up a binary search, you must always create a left `l` and a right `r` pointer. The left pointer points at the minimum value and the right points at the maximum; in this problem, it would be the max/min indices.

Repeatedly search until the left pointer exceeds the right.

The middle pointer is initialized with the middle value between the left and right pointers.

Then check two conditions:
*   If the value at the middle index is the target, `return mid`
*   If the value is less than the target, it is impossible for the target to be in the left portion of the list; this is known because the left portion is always smaller than the value at the middle index. Therefore, the left pointer is updated to the middle index + 1.
*   If neither of these conditions is true, then the value at the middle is greater than the target. Therefore, the right pointer is updated to the middle index - 1, for the inverse reason as the last condition.

If the `while` loop exists, the target is not within the input list.

## Algorithm Used

**Binary Search -** A search algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l = 0
        r = len(nums) - 1

        while l <= r:
            mid = (l+r)//2

            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                l = mid + 1
            else:
                r = mid - 1

        return -1
```