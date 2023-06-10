---
title: Largest Rectangle in Histogram
date: 2023-06-10 00:00:00 -400
categories: [Coding Questions, Hard]
tags: [python, stack]
---

### View *Largest Rectangle in Histogram* on [LeetCode](https://leetcode.com/problems/largest-rectangle-in-histogram/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n) - While the algorithm may iterate over the stack inside of the for loop, this is not common, and it will only happen once for that one element and those in the stack. This is because the algorithm pops the visited elements when iterating over the stack. Therefore, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - If all the heights in the list are in increasing order, then, at worse, the stack will store each element, resulting in the O(n) space complexity.

**Runtime Beats**  
96.28% of other submissions  

## Explanation
Before iterating through the input list, declare two variables, one to hold our max area and one to hold our stack. The stack is used to hold all the elements that are smaller than the current element.

Begin iterating through the stack and initialize our `start` variable to `i`. This variable will tell us where the "start" of the histogram starts. This must be a separate variable from `i` since the algorithm manipulates `i` and may shift it back to incorporate a height that exceeds the current one.

`While` the `stack` is non-empty and the current height is less than the last element of the stack:
*   Remove the last element from the stack and store its index and height
*   Update the max area, the area of the current histogram is calculated by multiplying the index of its starting point by the index of the height, which is smaller than it.
*   Update starts to be the index of the removed element. This is done to allow the algorithm to correctly incorporate the removed element's area.

When the `while` loop exists, add the start index and height to the stack.

When the `for` loop exits and the stack is non-empty, perform similar logic to the `while` loop. In the new `for` loop, when calculating the area, it uses the last index (`len(heights)`) because all elements remaining in the stack did not encounter any smaller elements, meaning their histogram extends until the end of the list.

When the new `for` loop exits, `return max_area`

## Data Structure Used

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to use any libraries.

**Visual Examples**  

Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view

## Solution  

```python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        max_area = 0
        stack = []

        for i,h in enumerate(heights):
            start = i
            while stack and h < stack[-1][1]:
                j, stack_h = stack.pop()
                max_area = max(max_area,(i - j) * stack_h)
                start = j
                    
            stack.append((start,h))

        for i,h in stack:
            max_area = max(max_area,(len(heights)-i)*h)

        return max_area
```