---
title: Shifting Letters
date: 2023-06-20 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, string]
---

### View *Shifting Letters* on [LeetCode](https://leetcode.com/problems/shifting-letters/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n + m) - The algorithm iterates through both lists, although at the same time, it must still access two separate places in memory, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n) - The algorithm stores the same number of characters as the input string in a list, resulting in the O(n) space complexity.

**Runtime Beats**  
92.15% of other submissions  

## Explanation  
Before iterating over the list, declare the array `ar` to store the shifted letters and `total_shift` to track the total number of times a character needs to shift.

Begin iterating from the last index to 0, since -1 is not included in this range, in steps of -1 (`len(s) - 1, -1, -1`).

Update `total_shift` to include the current shift, and shift the current character in `s.` The algorithm performs `%26` to reduce the total logic performed; without this, the algorithm would change the `if` statement into a while loop. This is due to 122 being the ASCII representation of `z` and the output only being able to contain characters a-z.

Once the character is correctly shifted, convert it to a character (`chr`) and append it to the array.

Once the for loop exists, join all the characters within the array in reverse order (`[::-1]`), and return the result.

## Solution  

```python
class Solution:
    def shiftingLetters(self, s: str, shifts: List[int]) -> str:
        ar = []
        total_shift = 0

        for i in range(len(s) - 1, -1, -1):
            total_shift += shifts[i]
            shifted_ascii = ord(s[i]) + total_shift%26
            
            if shifted_ascii > 122: shifted_ascii -= 26
    
            ar.append(chr(shifted_ascii))

        return ''.join(ar[::-1])
```