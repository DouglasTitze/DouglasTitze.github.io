---
title: Palindrome Number
date: 2023-05-29 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, two pointer]
---


### View *Palindrome Number* on [LeetCode](https://leetcode.com/problems/palindrome-number/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n) - Each number in `x` is visited at most twice, resulting in the O(n) time complexity. 
Since the multiple of two (2n) does not affect the growth rate of the function, it is not "counted" when analyzing the time complexity.

**Space Complexity**  
O(n) - Although we are replacing `x` with its string counterpart, we must still have n space in memory to allocate to the string before it replaces `x`, resulting in the O(n) space complexity.

## Explanation
Before iterating through the input number, we must convert it to a string and initialize our front (`f`) and end (`e`) pointers to their respective values.

After this, we enter a `while` loop until the front pointer exceeds the end pointer.

Inside this loop, we check if the front element is not equal to the end element.

*   If not equal, we `return False` because this number is no longer a palindrome.
*   If equal, we increment our pointers towards each other and continue to the next iteration.

If the while loop exists successfully, the input number is a valid palindrome, so we `return True`.

## Algorithm Description

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be if the elements are equal; if not, the input number is not a palindrome.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view

## Solution  

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        s = str(x)

        f = 0
        e = len(s)-1

        while f < e:
            if s[f] != s[e]: return False
            f +=1
            e -=1

        return True
```