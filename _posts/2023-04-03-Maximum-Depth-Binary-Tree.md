---
title: Maximum Depth of Binary Tree
date: 2023-04-03 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, depth-first search, binary tree]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/maximum-depth-of-binary-tree/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I quickly solved the problem and made it shorter and more elegant solution.

**What I Learned**  
I refreshed my memory about binary trees and their traversal.

**How I Can Improve**  
I believe I took the best approach possible, and the time spent was very reasonable.

**Comments**  
I can see how confident I have become with binary trees and traversing them. 
Two weeks ago, I was scared of binary tree questions and avoiding them, but now they seem so easy.  

Again LeetCode's solution statistics are inconsistent. 
The optimal answer is much shorter and includes fewer conditional statements, but it has a worse run time than my original. 

# Algorithm/Data Structure Description

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

**Visual Examples**  
Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view  

Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics For The Optimal Solution

**Time Spent Optimizing**  
5 Minutes

**Time Complexity**  
O(n) - The program explores every possible path/node, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Due to the recursive nature of my solution, it will continuously store a call of the function, and in the worst case, there would be one for every node, resulting in the O(n) space complexity.

**Runtime Beats**  
57.37% of other submissions  

**Memory Beats**  
50.64% of other sumbissions  

# Optimal Solution  

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if root == None:
            return 0

        # Reccursively iterate through each path when an empty root node  
        # is reached, return the value of that path, and compare it to the other  
        # path, get the maximum and continue passing that value upwards
        return max(self.maxDepth(root.left),self.maxDepth(root.right)) + 1
```

# Solution Statistics For The Original Solution

**Time Spent Coding**  
8 Minutes

**The time & space complexity are the same as the optimal.**

**Runtime Beats**  
95.88% of other submissions  

**Memory Beats**  
50.64% of other sumbissions  

# Solution  

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

	# If both left and right nodes exist, then explore both paths
        if root.left and root.right:
            return max(self.maxDepth(root.left)+1,self.maxDepth(root.right)+1)
	# If only a left path exists, then explore
        if root.left:
            return self.maxDepth(root.left)+1
	# If only a right path exists, then explore
        if root.right:
            return self.maxDepth(root.right)+1

	# If no path exists, then return
        return 1
```
