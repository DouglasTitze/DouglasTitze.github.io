---
title: Squares of a Sorted Array
date: 2023-09-06 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, sorting]
---

### View *Squares of a Sorted Array* on [LeetCode](https://leetcode.com/problems/squares-of-a-sorted-array/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n) - At most, 2 * n elements are visited, but since a constant multiple of n does not increase the growth rate, the final time complexity is O(n).

**Space Complexity**  
O(n) - A new list with n elements is created and then mutated into the final result, taking O(n) extra space.

**Runtime and Memory**  
_Due to the small dataset that LeetCode uses to test the program, the trivial solution is "more optimal."_

## Explanation  
_The comments explain the program_

## Algorithm Used

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be identifying which negative numbers (if any) will result in a larger squared value.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view


## Solution  

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        squares = [None] * len(nums)
        left, right = 0, len(nums) - 1

        # Increment from n to 0; this allows the numbers to be sorted in increasing order
        for i in range(len(nums)-1,-1,-1):

            # To accommodate for negative numbers, take the absolute values of both ends
            # If the left number is larger, replace squares[i] with the left number and increment left
            if abs(nums[left]) > abs(nums[right]):
                squares[i] = nums[left] ** 2
                left += 1
            
            # Similarly, do this with the right when it is the largest number
            else:
                squares[i] = nums[right] ** 2
                right -= 1

        return squares
```