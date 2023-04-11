---
title: Binary Tree Level Order Traversal
date: 2023-04-12 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [tree, binary tree, depth first search, breadth first search]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/binary-tree-level-order-traversal/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I implemented my solution quickly and had a very good runtime.

**What Went Wrong**  
I did not have a very good space complexity, becuase I solved this problem using a recurssive solution.

**What I Learned**  
I learned 

**How I Can Improve**  
I CAN...

**Comments**  
COMMENTS

# Algorithm Description

**Algorithm Name -** EXPLAIN

**Visual Examples**  
, [click](LINK_HERE){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
TIME minutes

**Time Complexity**  
O(x) - xxxxx, resulting in the O(n) space complexity.

**Space Complexity**  
O(x) - xxxx, resulting in the O(n) space complexity.

**Runtime Beats**  
91.90% of other submissions  

**Memory Beats**  
16.32% of other sumbissions  

# Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None: return []

        self.order = []

        def search(root,depth):
            if len(self.order) == depth:
                self.order.append([root.val])
            else:
                self.order[depth].append(root.val)

            if root.left: search(root.left,depth+1)
            if root.right: search(root.right,depth+1)

        search(root,0)
        return self.order
```
