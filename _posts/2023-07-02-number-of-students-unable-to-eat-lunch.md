---
title: Number of Students Unable to Eat Lunch
date: 2023-07-02 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, stack, queue]
---

### View *Number of Students Unable to Eat Lunch* on [LeetCode](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - The expected time complexity is some multiple of n, the multiple varies depending on the input lists, but since multiples of n do not increase the big-O complexity the reported time complexity is O(n).

**Space Complexity**  
O(n) - Every student must be stored in the queue, resulting in the O(n) space complexity.

**Runtime Beats**  
48.79% of other submissions  

## Explanation  
The program follows the following pattern:

1.  Record the length of the queue before iteration and store it in `before_loop`    
2.  Iterate through `before_loop` elements    
**For each element, execute the following steps**    
3.  Check if the first element in the queue is equal to sandwich at the top of the stack  
    *  If they are equal, remove the student from the queue and the sandwitch from the stack
    *  Else, remove the student from the front of the queue and place him in the back of the queue
4.  When the for loop of `before_loop` ends, check  
    *  `if before_loop == len(queue):` If no elements were removed, then return `before_loop`, since this number is equal to the number of students unable to eat.
    *  `else:` Go to step 1
5.  If the queue is depleted the while loop will fail to execute meaning all students were able to eat, `return 0`.

## Data Structures Used  

**Queue -** A container that holds elements and follows the First In First Out (FIFO) principle, only allowing removal from the front of the container and additions to the back.

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to use any libraries, simply reverse `sandwiches`.

**Visual Examples**  
Visual representation of a queue, [click](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221213113312/Queue-Data-Structures.png){:target="_blank"} to view.

Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view


## Solution  

```python
class Solution:
    def countStudents(self, students: List[int], sandwiches: List[int]) -> int:
        queue = deque()
        for s in students: queue.append(s)

        sandwiches.reverse()

        before_loop = len(queue)

        while queue:
            for _ in range(before_loop):
                if queue[0] == sandwiches[-1]:
                    sandwiches.pop()
                    queue.popleft()
                else: 
                    queue.append(queue.popleft())

            else:
                if before_loop == len(queue):
                    return before_loop
                else:
                    before_loop = len(queue)

        return 0
```