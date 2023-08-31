---
title: Minimum Time Difference
date: 2023-08-31 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, math, string]
---

### View *Minimum Time Difference* on [LeetCode](https://leetcode.com/problems/minimum-time-difference/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n<sup>2</sup>) - For every element at index i, its difference is calculated with the elements in the range i+1 to n, resulting in the O(n<sup>2</sup>) time complexity.

**Space Complexity**  
O(1) - No extra space is required to run this program since the converted values replace their string counterparts, resulting in the O(1) space complexity.

**Runtime Beats**  
90.32% of other submissions  

**Memory Beats**  
89.41% of other sumbissions  

## Explanation  
For each element at index i, it calculates the difference between it and the elements in the range i+1 to n.    

If the difference is greater than 12 hours, then the shortest time difference is no longer forward in time but backward, e.g. 00:00 to 23:59. Forward, this would be a difference of 23 hours and 59 minutes, but backward, this would only be a difference of 1 minute.

## Solution  

```python
class Solution:
    def str_to_int(self,t):
        h = t[:2]
        m = t[3:]

        return int(m) + int(h) * 60

    def findMinDifference(self, timePoints: List[str]) -> int:
        length = len(timePoints)
        day = 1440
        min_time = 1441

        # Convert the first element into an integer before the for loop to avoid checking its type within the first for loop.
        timePoints[0] = self.str_to_int(timePoints[0]) 
        for i in range(length - 1):
            t1 = timePoints[i]
            for j in range(i+1,length):

                # If the element is a str, convert it to an int
                if isinstance(timePoints[j],str): 
                    timePoints[j] = self.str_to_int(timePoints[j])
                t2 = timePoints[j]

                diff = abs(t1-t2)

                # Exit early if a difference of 0 is found
                if diff == 0:
                    return 0

                # Differences under 12 hours (720 minutes) benefit from going forwards in time
                elif diff < 720: 
                    min_time = min(min_time, diff)
                
                # Differences greater than 12 hours benefit from going backward in time
                else: 
                    min_time = min(min_time, day - diff)

        return min_time
```