---
title: Maximum Number of Balloons
date: 2023-07-16 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, counting, hash map]
---

### View *Maximum Number of Balloons* on [LeetCode](https://leetcode.com/problems/maximum-number-of-balloons/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Each character from the input string must be seen, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Although a dictionary is declared, it will only ever contain five characters, resulting in the O(1) space complexity.

**Runtime Beats**  
94.45% of other submissions  

**Memory Beats**  
74.33% of other sumbissions  

## Explanation  
The algorithm counts the frequency of each character and stores it in `char_counter.`    

The algorithm then keeps track of the smallest frequency out of all the characters in "balon" because we can only make as many "balloon" strings as the smallest frequency permits. To accommodate for the double characters "o" and "l," we floor the frequency of their appearances by a factor of 2.  

Finally, we return the `count`.

## Solution  

```python
class Solution:
    def maxNumberOfBalloons(self, text: str) -> int:
        char_counter = Counter(text)

        freq = float("inf")
        for c in "balon":
            if c is 'l' or c is 'o':
                freq = min(freq, char_counter[c]//2)
            else:
                freq = min(freq, char_counter[c])
        return freq
```