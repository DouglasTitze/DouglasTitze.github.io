---
title: Find the Town Judge
date: 2023-07-25 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, graph]
---

### View *Find the Town Judge* on [LeetCode](https://leetcode.com/problems/find-the-town-judge/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - We must iterate through all the people in the town twice, but multiples of the growth factor do not affect the time complexity, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each person and their connections must be recorded in the list, resulting in the O(n) space complexity.

**Runtime Beats**  
93.37% of other submissions  

**Memory Beats**  
60.72% of other sumbissions  

## Explanation  
Each person in the town is initialized to be trusted by 0 people, and as the algorithm iterates through the graph, the number of people who trust them is updated.

If person `a` trusts person `b,` then we must decrement person `a`, denoting that they are not the judge since they trust someone, and we must increment person `b,` denoting that someone trusts them.

Once the `trust` list has been fully iterated, only one person will be trusted by `n-1` people; therefore, they are the only valid judge. In the edge case where there are more than one persons that are trusted but do not trust anyone, the algorithm will correctly identify this since neither person will be trusted by `n-1` people. There is no judge.

## Solution  

```python
class Solution:
    def findJudge(self, n: int, trust: List[List[int]]) -> int:
        if n == 1: return 1
        
        trusted = [0] * (n+1)
        for a,b in trust:
            trusted[a] -= 1
            trusted[b] += 1

        for i,v in enumerate(trusted):
            if v == n-1: 
                return i

        return -1
```