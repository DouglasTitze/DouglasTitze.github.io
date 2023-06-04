---
title: Trapping Rain Water
date: 2023-06-04 00:00:00 -400
categories: [Coding Questions, Hard]
tags: [python, two pointer]
---

### View *Trapping Rain Water* on [LeetCode](https://leetcode.com/problems/trapping-rain-water/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n) - The program iterates through each element in the input list, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the input list, resulting in the O(1) space complexity.

**Runtime Beats**  
69.18% of other submissions  

**Memory Beats**  
61.67% of other sumbissions  

## Explanation
Before searching the list, initialize all the variables: `trapped_water` to 0, `l` and `r` to their respective maximum, and `max_l` and `max_r` to the current maximum for the left and right pointers.

The `while` loop will run until `l` meets or exceeds `r.`

During each loop, check the list's current maximums at the left and right sides.

*   If the right maximum is smaller, decrement r, and check if the current right maximum `max_r` is larger than the new element at `r.`   

    *   If the new element is larger, replace the maximum right with the new element. 
    *   Else, update `trapped_water`; this is because the `max_l` is larger than `max_r` and `max_r` is larger than the new element at `r`; therefore, add the difference between the `max_r` and the element at `r`.  

*   Else, perform steps similar to the first conditional statement except interchange all left and right values and increment `l` instead of decrementing.

Once the `while` loop exists, `return trapped_water`.



## Algorithm Description

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be if the maximum left element is less than the maximum right element.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view

## Solution  

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        trapped_water = 0
        l, r = 0, len(height) - 1
        max_l, max_r = height[l], height[r]

        while l < r:
            if max_l >= max_r:
                r -= 1

                if height[r] >= max_r:
                    max_r = height[r]
                else:
                    trapped_water += max_r - height[r]

            else:
                l += 1

                if height[l] >= max_l:
                    max_l = height[l]
                else:
                    trapped_water += max_l - height[l]

        return trapped_water
```