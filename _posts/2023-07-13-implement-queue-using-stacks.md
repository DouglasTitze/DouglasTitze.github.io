---
title: Implement Queue using Stacks
date: 2023-07-13 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, stack, queue]
---

### View *Implement Queue using Stacks* on [LeetCode](https://leetcode.com/problems/implement-queue-using-stacks/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(1) - All operations perform at an amortized (expected) rate of O(1) because if multiple push or pop operations are called in, succession of the first may take long, but the rest are O(1).

**Space Complexity**  
O(n) - Every element pushed onto the stack is stored in a variable, resulting in the O(n) space complexity.

**Runtime Beats**  
97.51% of other submissions  

**Memory Beats**  
75.34% of other sumbissions  

## Explanation  
To achieve an amortized O(1) execution time for push and pop, we must flip the order of the stack by moving all the elements from the opposing stack to the correct stack; from there, all concurrent operations are O(1). While the first operation may take a lot of time, the other will all be O(1).

If the user calls the push method, check:

1. `while self._pop:` If any elements are in the `_pop` stack, then remove them all and place them in the `_push` stack in reverse order
2. Finally, append the input element to the `_push` stack

If the user calls the pop method, check:

1. `while self._push:` If any elements are in the `_push` stack, then remove them all and place them in the `_pop` stack in reverse order
2. Finally, pop the last input element in the `_pop` stack

If the user calls the peek method, check:

* `if self._pop:` If the `_pop` stack is non-empty, return the last element
* `else:` Return the first element of the `_push` stack

If the user calls the empty method:

* `self._push == self._pop` If the stacks are equal to each other, they must both be empty.

## Data Structures Used  

**Queue -** A container that holds elements and follows the First In First Out (FIFO) principle, only allowing removal from the front of the container and additions to the back.  

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.    

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to import any libraries.  

**Visual Examples**  
Visual representation of a queue, [click](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221213113312/Queue-Data-Structures.png){:target="_blank"} to view.  

Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view  
  
## Solution  

```python
class MyQueue:

    def __init__(self):
        self._push = []
        self._pop = []

    def push(self, x: int) -> None:
        while self._pop:
            self._push.append(self._pop.pop())

        self._push.append(x)

    def pop(self) -> int:
        while self._push:
            self._pop.append(self._push.pop())

        return self._pop.pop()

    def peek(self) -> int:
        if self._pop:
            return self._pop[-1]
        
        else:
            return self._push[0]

    def empty(self) -> bool:
        return self._push == self._pop

```