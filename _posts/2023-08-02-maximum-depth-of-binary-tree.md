---
title: Maximum Depth of Binary Tree
date: 2023-08-02 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, binary tree]
---

### View *Maximum Depth of Binary Tree* on [LeetCode](https://leetcode.com/problems/maximum-depth-of-binary-tree/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Every node in the tree is visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Since the algorithm uses reccursive calls it results in at most O(n) memory to store all the reccursive calls.

**Runtime Beats**  
99.70% of other submissions  

**Memory Beats**  
100% of other sumbissions  

## Explanation  
The algorihtm reccursively calls the `maxDepth` function on each node, and for every node that is not `Null` or `None` it adds one to the maximum depth and continiues to call itself on the children of each node.

## Algorithm Used  

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Visual Examples**  
Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view  


## Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root == None:
            return 0

        return max(self.maxDepth(root.left),self.maxDepth(root.right)) + 1
```