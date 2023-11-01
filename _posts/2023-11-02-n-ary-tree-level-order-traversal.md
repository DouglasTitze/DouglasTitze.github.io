---
title: N-ary Tree Level Order Traversal
date: 2023-11-02 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, tree]
---

### View *N-ary Tree Level Order Traversal* on [LeetCode](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Each node in the tree must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each value at every node must be stored, resulting in the O(n) space complexity.

**Runtime Beats**  
97.63% of other submissions  

**Memory Beats**  
80.81% of other sumbissions  

## Explanation  


## Data Structures Used  

**Tree -** A hierarchical data structure where each data point is a node and can have childen and/or parent nodes connected to it.

**Queue -** A container that holds elements and follows the First In First Out (FIFO) principle, only allowing removal from the front of the container and additions to the back. 

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
Creates a queue of elements yet to be visited and then iterates through each level (or elements with similar properties) until there are no more elements of the same level. 

**Visual Examples**  
Visual representation of a queue, [click](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20221213113312/Queue-Data-Structures.png){:target="_blank"} to view.  

## Solution  

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""
from collections import deque

class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if root == [] or root == None: return []
        
        que = deque()
        que.append(root)

        levels = []

        while que:
            curLevel = []
            for _ in range(len(que)):
                curNode = que.popleft()
                curLevel.append(curNode.val)

                for child in curNode.children:
                    if child != None:
                        que.append(child)
            levels.append(curLevel)

        return levels
```