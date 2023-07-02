---
title: Teemo Attacking
date: 2023-07-01 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array]
---

### View *Teemo Attacking* on [LeetCode](https://leetcode.com/problems/teemo-attacking/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Every time in the input list must be iterated over, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables declared is constant and independent from the input list, resulting in the O(1) space complexity.

**Runtime Beats**  
99.9% of other submissions  

**Memory Beats**  
97.36% of other sumbissions  

## Explanation  
To accurately calculate the sum of the time the enemy is poisoned the last time poisoned and the end duration of that poison attack must be tracked. Beginning those two variables at impossible values allows for an easy comparison of two things:

*   `if end_duration < cur_t:` If the end of the first attack has ended, then the full duration can be added to the sum
*   `else:` Their full duration did not complete, resulting in `cur_t - last_t` time being added to the sum.

Once the addition is complete, update the end duration and the last time to their new values.

When the for loop iterates through all the times, return the sum.

## Solution  

```python
class Solution:
    def findPoisonedDuration(self, timeSeries: List[int], duration: int) -> int:
        sum_time = 0
        last_t = -1
        end_duration = -1

        for cur_t in timeSeries:
            if end_duration < cur_t:
                sum_time += duration
                
            else:
                sum_time += cur_t - last_t

            end_duration = cur_t + duration
            last_t = cur_t
            

        return sum_time
```