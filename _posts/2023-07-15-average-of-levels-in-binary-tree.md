---
title: Average of Levels in Binary Tree
date: 2023-07-15 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, breadth-first search, binary tree]
---

### View *Average of Levels in Binary Tree* on [LeetCode](https://leetcode.com/problems/average-of-levels-in-binary-tree/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - Every node in the tree must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(l) - The queue will have at most `l` elements, where `l` is the number of nodes in the largest level, resulting in the O(l) space complexity.

**Runtime Beats**  
76.22% of other submissions  

**Memory Beats**  
73.90% of other sumbissions  

## Explanation  
The algorithm follows the breadth-first search algorithm and creates a queue of all nodes at the same level, iterates through exactly the number of elements at that level, and increments the `cur_sum` variable while removing each node from the queue. At the same time, it is appending children nodes not equal to `None` to the back of the queue to be iterated through on the next loop (the next level). Once the current level is exhausted, the algorithm divides the `cur_sum` by the number of elements in that level to get the average and then adds that value to the result list. Finally, when no nodes are left in the queue, the algorithm returns the result list.

## Algorithm & Data Structure Used  

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
Create a queue of elements yet to be visited and then iterate through each level (similar properties) until there are no more elements of the same level. 

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.  


## Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        q = deque()
        q.append(root)
        res = []

        while q:
            cur_sum = 0
            len_q = len(q)
            for _ in range(len_q):
                    n = q.popleft()
                    cur_sum += n.val
                    if n.left: q.append(n.left)
                    if n.right: q.append(n.right)

            res.append(cur_sum/len_q)

        return res
```