---
title: Integer Replacement
date: 2023-06-08 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, recursion]
---

### View *Integer Replacement* on [LeetCode](https://leetcode.com/problems/integer-replacement/description/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
16 minutes

**Time Complexity**  
O(log(n)) - For the majority of iterations, `n` is divided in half, resulting in the O(log(n)) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity. If the recursive function calls count towards the space complexity, then it would be O(2 * log(n)) -> O(log(n)) since Big-O ignores constant multiples of the growth rate.

## Explanation
**This solution is not the most optimal, but arguably it is the most intuitive. The most optimal solutions utilize bit manipulation and are complex to understand and create on-demand**

Creating the recursive function requires a base case and logic to reduce its inputs.

The base case is `if n==1: return 0` because 1 is the number `n` needs to reach.

The other conditional statements determine which operation will get `n` to 1 the fastest.
*   `if n%2==0:` If the number is a factor of 2, then to get `n` to 1 as fast as possible, `n` should be divided by 2.
*   `else:` Otherwise, `n` is odd and must be incremented or decremented to become a factor of 2. This can be done by performing both the incrementation and decrementation and returning the smallest.

The algorithm continuously loops through the base case and the conditional statements until the correct result is returned.

## Algorithm Used

**Recursion  -** A function which calls itself contains a base case and logic that decreases the received inputs.

The base case is when n==1, and every other case recursively calls `integerReplacement` until `n` is reduced to 1.

## Solution  

```python
class Solution:
    def integerReplacement(self, n: int) -> int:
        if n==1: return 0

        if n%2==0:
            return self.integerReplacement(n//2)+1
        else:
            add=self.integerReplacement(n+1)
            minus=self.integerReplacement(n-1)
            return min(add,minus)+1
```