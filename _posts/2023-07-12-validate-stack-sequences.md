---
title: Validate Stack Sequences
date: 2023-07-12 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, stack]
---

### View *Validate Stack Sequences* on [LeetCode](https://leetcode.com/problems/validate-stack-sequences/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**   
15 minutes

**Time Complexity**  
O(n + m) - Each element from the inputs list will be visited at most twice, but that does not increase the growth rate, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n) - Every element from the `pushed` input list may be stored in the stack, resulting in the O(n) space complexity.

**Runtime Beats**  
76.67% of other submissions  

**Memory Beats**  
96.40% of other sumbissions  

## Explanation  
Iterate through the `pushed` list and append every element onto the stack. During this iteration, enter a while loop until there are no elements left in the stack or the last element of the stack does not match the ith element of the popped list. If they match, increment the popped list and remove the last element from the stack.

Once the for loop terminates, check if any elements remain in the stack. The input lists are not a valid stack sequence if any elements remain.

## Data Structure Used  

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.  

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to import any libraries.

**Visual Examples**  
Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view


## Solution  

```python
class Solution:
    def validateStackSequences(self, pushed: List[int], popped: List[int]) -> bool:
        i = 0
        stack = []
        for elm in pushed:
            stack.append(elm)
            while stack and popped[i] == stack[-1]:
                stack.pop()
                i+=1
        return not stack
```