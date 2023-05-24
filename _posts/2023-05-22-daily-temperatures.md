---
title: Daily Temperatures
date: 2023-05-22 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, stack, array]
---


### View *Daily Temperatures* on [LeetCode](https://leetcode.com/problems/daily-temperatures/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n) - We must iterate through the `temperatures` list, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst-case scenario, the numbers in the `temperatures` list decrease. 
Meaning, each element from `temperatures` would be in the `stack`, resulting in the O(n) space complexity.

**Runtime Beats**  
97.62% of other submissions  

**Memory Beats**  
43.51% of other sumbissions  

## Explanation
Before iterating through `temperatures,` we must initialize our result list (`res`) with all 0's because this is our default value in the worst-case scenario. 
We must also declare our `stack` list. 
For this problem, our stack will store the index of temperatures that are less than what is inside of the stack, e.g., a stack of the indexes of temperatures in decreasing order measured by the temperatures at each index.

We begin iterating through the `temperatures` list using `for i, t in enumerate(temperatures):` this allows us to iterate through `temperatures` and access the index (`i`) and temperature (`t`) for each element.

During each iteration, we will check if the `stack` is non-empty. If so, then we will also check if the current temperature `t` is greater than the temperature at the index of the last element in the `stack.`

If both conditions are satisfied, we will continue to loop until they are not. 
While inside this loop, we will store the index of the temperature in `stack_i` by removing it from the stack and then altering the result list's value at that index by taking the difference between the current index and the index of the new largest temperature. 
This "equation" allows us to determine how many indices it took from the poped temperature to a temperature larger than it.

Once we exit the `while` loop, we will append the current index to the `stack.`

We will return the result list once we exit the `for` loop.

## Data Structure Used

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to use any libraries.

**Visual Examples**
Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view

## Solution  

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        res = [0] * len(temperatures)
        stack = []

        for i, t in enumerate(temperatures):
            while stack and t > temperatures[stack[-1]]:
                stack_i = stack.pop()
                res[stack_i] = (i - stack_i)

            stack.append(i)

        return res
```