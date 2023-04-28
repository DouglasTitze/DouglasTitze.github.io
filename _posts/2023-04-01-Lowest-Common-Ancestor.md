---
title: Lowest Common Ancestor of a Binary Search Tree
date: 2023-04-01 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search tree, depth-first search]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I was able to solve the problem much faster than I expected and recalled how to find ancestors.

**What Went Wrong**  
I did not optimize my code.

**What I Learned**  
I refreshed my memory on binary search trees and how to search for ancestors.

**How I Can Improve**  
I must allow time after each question to analyze my code and look for flaws. 
Looking at my original solution, I see many ways to reduce it. 
By allowing myself self-time to refine my code, I can help improve future implementations and familiarize myself with a scenario I may encounter during a coding interview.

**Comments**  
Although I only briefly glanced at another user's submission, it instantly made me think of how to alter mine to achieve a similar code structure. 
So, I cannot accurately say it only took me "2 minutes" to optimize my code because I even started getting confused looking at my original solution.

# Algorithm Description

**Binary Search Tree -** A sorted and ordered tree based on the root node. Subtrees to the left of ANY node are less than their parent, and those to the right are greater.

**Lowest Common Ancestor -** The deepest node that is a parent of both nodes. In this problem, a node can be its parent if one of its children is the other node.

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

**Visual Examples**  
Binary Search Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/bst-vs-not-bst.png){:target="_blank"} to view  

Depiction of the lowest common ancestor, [click](https://files.codingninjas.in/lca_ex1-6383.png){:target="_blank"} to view

Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics For The Optimal Solution

**Time Complexity**  
O(h) - The program can only iterate downwards from 0 (root) to h (the deepest node), resulting in the O(h) time complexity.

**Space Complexity**  
O(h) - Every iteration creates three new variables per recursive call, and in the worst case, that would be h times, resulting in the O(h) space complexity.  

**Runtime Beats**  
80.32% of other submissions  

**Memory Beats**  
96.36% of other sumbissions  

# Optimal Solution

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
            # If the parent is greater than both target nodes, we must search the left branch
            if root.val > q.val and root.val > p.val:
                return self.lowestCommonAncestor(root.left,p,q)
            # If the parent is less than both target nodes, we must search the right branch
            elif root.val < q.val and root.val < p.val:
                return self.lowestCommonAncestor(root.right,p,q)
            # In all other cases, the root is the lowest common ancestor
            else:
                return root
```

# Solution Statistics For The Original Solution

**Time Spent Coding**  
13 minutes

**The time & space complexity are the same as the optimal.**

**Runtime Beats**  
76.17% of other submissions  

**Memory Beats**  
57.88% of other sumbissions  

# Original Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
            # Recurssive method
            def find(root,q,p):
                # Place values in variables to reduce repetitive calls to the same variables    
                root_val = root.val
                q_val     = q.val
                p_val     = p.val

                # If the root is equal to one of the target nodes
                if root == q or root == q:
                    # Check the left child is a target node
                    if root.left:
                        if root.left == p or root.left == q:
                            return root
                    # Check the right child is a target node
                    if root.right:
                        if root.right == p or root.left == q:
                            return root

                # If the root is in between the target nodes, return the root
                if (root_val > q_val and root_val < p_val) or (root_val < q_val and root_val > p_val):   
                    return root

                # If the parent is greater than both target nodes, we must search the left branch
                if root_val > q_val and root_val > p_val:
                    root = find(root.left,p,q)

                # If the parent is less than both target nodes, we must search the right branch
                elif root_val < q_val and root_val < p_val:
                    root = find(root.right,p,q)
                
                return root
            
            # Begin the search, and return when found
            return find(root,p,q)
```
