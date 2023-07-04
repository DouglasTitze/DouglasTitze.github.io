---
title: Baseball Game
date: 2023-07-04 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, math]
---

### View *Baseball Game* on [LeetCode](https://leetcode.com/problems/baseball-game/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - The input list is iterated through once, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - In the worst case, the most numbers we will have in the `score` list is the same as the input `operations` list, resulting in the O(n) space complexity.

**Runtime Beats**  
76.28% of other submissions  

**Memory Beats**  
78.40% of other sumbissions  

## Explanation  
The algorithm implements the steps asked by the problem for each operation in the input list:

1.    `if op == "+":` Add the last and the second last score together, then append it to the list
2.    `elif op == "D":` Double the last score and append it to the list
3.    `elif op == "C":` Remove the last score from the list
4.    `else:` Add the new score to the list

Once all the elements from the input list are seen, return the sum of the `score` list.

## Solution  

```python
class Solution:
    def calPoints(self, operations: List[str]) -> int:
        score = []

        for op in operations:
            if op == "+":
                score.append(score[-1] + score[-2])
            elif op == "D":
                score.append(score[-1] * 2)
            elif op == "C":
                score.pop()
            else:
                score.append(int(op))

        return sum(score)
```