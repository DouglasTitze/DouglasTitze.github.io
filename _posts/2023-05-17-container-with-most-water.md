---
title: Container With Most Water
date: 2023-05-17 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, two pointer]
---


### View *Container With Most Water* on [LeetCode](https://leetcode.com/problems/container-with-most-water/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
12 minutes

**Time Complexity**  
O(n) - We only iterate through each element once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

**Runtime Beats**  
74.55% of other submissions  

**Memory Beats**  
31.72% of other sumbissions  

## Explanation
Before iterating through the list, we must initialize our "pointers," `left` and `right`. 
We will set both of these variables to their respective values. 
We must also create a variable to store the maximum amount of water a container can store called `most`.  

We will iterate through the input list if the `left` pointer is less than the `right` pointer, ensuring we do not iterate over the same element twice.

We will store the current height at each pointer in their respective variables `left_h` and `right_h` and then compute the smallest height and store it in `smallest_h`. 
Using these variables, we will replace the value in `most` with the largest value out of `most` and the computed maximum amount of water the current container can store `smallest_h * (right-left)`.

We then must iterate the pointer with the smallest height to the next element, and if they are equal, decrement the right pointer to avoid extra logic. We do this because if both are equal, it does not matter which pointer is incremented/decremented.

When the while loop exits, we will have the maximum amount of water we can store in the variable `most`, and then return it.

## Algorithm Description

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be the largest amount of water stored between the containers, and beginning at each extreme allows us to compute this in one iteration of the list.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view  

## Solution  

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        left = 0
        right = len(height) - 1

        most = 0

        while left < right:
            left_h = height[left]
            right_h = height[right]
            smallest_h = min(left_h,right_h)

            most = max(most, smallest_h * (right-left))

            if left_h < right_h:
                left +=1
            else:
                right -=1

        return most
```