---
title: Maximal Network Rank
date: 2023-07-20 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, graph]
---

### View *Maximal Network Rank* on [LeetCode](https://leetcode.com/problems/maximal-network-rank/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n<sup>2</sup>) - Each possible pair in the graph must be visited, resulting in the O(n<sup>2</sup>) time complexity.

**Space Complexity**  
O(n<sup>n</sup>) - In the worst case, each node is connected, making each node stored n times, resulting in the O(n<sup>n</sup>) space complexity.

**Runtime Beats**  
68.91% of other submissions  

## Explanation  
_Comments explain the algorithm_

## Solution  

```python
class Solution:
    def maximalNetworkRank(self, n: int, roads: List[List[int]]) -> int:
        dic = {}

        # Create a dictionary of empty sets for each possible node
        for i in range(n):
            dic[i] = set()

        # Add each node to each other set
        for c1, c2 in roads:
            dic[c1].add(c2)
            dic[c2].add(c1)

        max_net = 0

        # Double for loop allows for each pair of nodes to be checked
        for i in range(n-1):
            for j in range(i+1,n):

                # The length of both sets is their maximum network
                tot = len(dic[i]) + len(dic[j])

                # If the pair is connected, then subtract one to account for the duplicate
                if i in dic[j]: tot -= 1

                # Update max_net if tot is greater than the current max_net
                max_net = max(tot,max_net)

        return max_net
```