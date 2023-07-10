---
title: Invert Binary Tree
date: 2023-07-09 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, binary tree, depth-first search]
---

### View *Invert Binary Tree* on [LeetCode](https://leetcode.com/problems/invert-binary-tree/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - Every node in the tree is visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The `invertTree` method is called on all nodes, but these recursive calls must be stored on the stack, resulting in the O(n) space complexity.

**Runtime Beats**  
91.10% of other submissions  

**Memory Beats**  
73.71% of other sumbissions  

## Explanation  
The algorithm works recursively by switching the nodes after the deepest recursive call has terminated.

The steps in this algorithm are:
1. `if not root:` If the root is None, return the root.
2. Recursively call `invertTree` on the left and right nodes
3. Re-assign the input root nodes to their inverse.

This algorithm works since the recursive calls terminate in a depth-first search fashion allowing for the re-assigning of nodes to occur only once the root nodes' children (and their children) have been inverted.

# Algorithm Used

**Depth-First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

**Visual Examples**  
Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view


## Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root: return root

        left = self.invertTree(root.left)
        right = self.invertTree(root.right)

        root.left = right
        root.right = left

        return root
```