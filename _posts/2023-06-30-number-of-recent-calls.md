---
title: Number of Recent Calls
date: 2023-06-30 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, queue]
---

### View *Number of Recent Calls* on [LeetCode](https://leetcode.com/problems/number-of-recent-calls/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n) - In the worst case, over 3000ms will have passed since the last ping resulting in the entire queue being searched through and popped from, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Every ping is stored in the queue; technically, the argument could be made that, at worst, the queue has 3000 elements, but ignoring that the space complexity is O(n).

**Runtime Beats**  
89.51% of other submissions  

**Memory Beats**  
80.52% of other sumbissions  

## Explanation  
The initialization method declares an empty deque to the variable queue and nothing else.

The ping method takes in a number greater than the last entered, and knowing this allows for easier removal from the queue. 

Every number entered is appended to the queue, and then a bottom variable is created to denote the lowest possible time value allowed in the queue. Using this value, the while loop iterates over the queue and checks:

1.   `if self.queue[0] < bottom:` If the last element is less than our `bottom` value, remove it.
2.   `else:` The queue is valid; break out of the loop.

When the while loop exits, the number of elements within the queue is the total number of operations within the inclusive range `[t - 3000, t]`

## Data Structure Used  

**Queue -** A container that holds elements and follows the First In First Out (FIFO) principle, only allowing removal from the front of the container and additions to the back.

**Visual Examples**  
Visual representation of a queue, [click](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221213113312/Queue-Data-Structures.png){:target="_blank"} to view.


## Solution  

```python
class RecentCounter:

    def __init__(self):
        self.queue = deque()

    def ping(self, num):
        self.queue.append(num)
        bottom = num - 3000

        while True:
            if self.queue[0] < bottom:
                self.queue.popleft()
            else:
                break

        return len(self.queue)
        
```