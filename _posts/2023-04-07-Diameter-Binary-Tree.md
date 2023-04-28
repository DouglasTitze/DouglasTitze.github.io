---
title: Diameter of Binary Tree
date: 2023-04-07 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, depth-first search, binary tree]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/diameter-of-binary-tree/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I was able to undestand the problem and create a near functional program.

**What Went Wrong**  
I could not figure out trees with two nodes kept giving me a result off by one.

**What I Learned**  
I learned how to find the diameter of a tree and got some practice in with depth first search.

**How I Can Improve**  
Practice more, if I had more experience with trees and algorithms I might have been able to solve the problem. 
I also would have benifit from saving my original solution instead of completely deleteing it, this may have helped me combine my two semi working programs into one that was fully functional.

**Comments**  
I knew the algorithm to follow and how to implement it, but one of my test cases kept incorrectly adding one to my result. 
Unfortunately, even after scrapping my code and starting from scratch, my logic began work only for trees with two nodes.

# Data Structure Description

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Visual Examples**  
Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view  

# Solution Statistics  

**Time Complexity**  
O(n) - We must iterate through each node in the tree before we are able to definitively say we have encountered the diameter (the longest path between two nodes), resulting in the O(n) time complexity

**Space Complexity**  
O(n) - This implementation uses a recurrsive function which is also called on every node, resulting in the O(n) space complexity.

**Runtime Beats**  
90.46% of other submissions  

**Memory Beats**  
73.55% of other sumbissions  

# Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        self.diam = 0

        def dps(root):
            if root == None: return 0

            l = dps(root.left)
            r = dps(root.right)

            # Assign diamater to the greatest diameter diam or current diameter (l+r)
            self.diam = max(self.diam,l+r)
            
            # Return the deepest child
            return max(l,r) + 1

        dps(root)
        return self.diam
```
