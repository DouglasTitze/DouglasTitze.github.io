---
title: Generate Parentheses
date: 2023-06-05 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, string, backtracking]
---

### View *Generate Parentheses* on [LeetCode](https://leetcode.com/problems/generate-parentheses/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(2<sup>n</sup>) - The algorithm must explore each possible combination of strings of length 2n, resulting in 2<sup>2n</sup> time, but big-O ignores constant multiples, resulting in the O(2<sup>n</sup>) time complexity.

**Space Complexity**  
O((2n)!/ (n! * (n + 1)!)) - The maximum space for all the strings can be represented by is represented by this formula.

**Runtime Beats**  
74.89% of other submissions  

**Memory Beats**  
68.87% of other sumbissions  

## Explanation
The algorithm implements a recursive method `backtrack` and takes in three parameters: two integers representing the number of `open` and `close` parenthesis, and one string `s`. This method contains three conditional statements.


*  `if len(s) == n * 2:` When executed, the string is at the maximum length and must be appended to the list, and this backtrack path must terminate.

*  `if open < n:` To execute, there must be fewer open parentheses than the maximum amount `n.` When executed, a new branch of `backtrack` is created, exploring all possible paths with `open + 1` open parenthesis.


*  `if close < open:`To execute, there must be fewer close parentheses than open parentheses. When executed, a new branch of `backtrack` is created, exploring all possible paths with `close + 1` close parenthesis.

Once the `backtrack` method is declared, create a list to contain all the output strings. 
After this, begin the backtracking algorithm with the input number of `open` and `close` parenthesis to 0 and the beginning string to an empty string.

## Algorithm Used

**Backtracking -** An algorithmic technique that incrementally builds possible solutions by exploring all possible paths at each increment.

**Visual Examples**  
Visualization of generate parentheses backtracking, [click](https://miro.medium.com/v2/resize:fit:720/format:webp/1*a932yah98FuImJH_-JCsvA.png){:target="_blank"} to view.

## Solution  

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        def backtrack(open, close, s):
            if len(s) == n * 2:
                res.append(s)
                return 

            if open < n:
                backtrack(open + 1, close, s + '(')

            if close < open:
                backtrack(open, close + 1, s + ')')

        res = []
        backtrack(0, 0, '')
        return res
```