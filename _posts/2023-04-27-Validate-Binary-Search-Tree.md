---
title: Validate Binary Search Tree
date: 2023-04-27 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search tree, depth-first search]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/validate-binary-search-tree/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I was able to complete the problem after a few different approaches.

**What Went Wrong**  
I was having a hard time putting my thoughts into code. 
Identifying the easiest and most efficient way to check each condition was difficult.

**What I Learned**  
I have gained more experience practicing two essential algorithms and data structures.

**Comments**  
The solution statistics for this problem are entirely broken because all the solutions are almost identical.
This causes the same answer to sway from 95% to 5%.

# Algorithm Description

**Binary Search Tree -** A sorted and ordered tree based on the root node. Subtrees to the left of ANY node are less than their parent, and those to the right are greater.

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

**Visual Examples**  
Binary Search Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/bst-vs-not-bst.png){:target="_blank"} to view  

Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
25 minutes

**Time Complexity**  
O(n) - We only need to iterate through each element in the binary search tree once, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each recursive call has two variables, and the recursive function is called on each node, resulting in an O(2 * n) space complexity. 
Since big O ignores constant multiples of n, the "real" space complexity is O(n).

# Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def valid(lB,rB,root):
            if not root: return True
            
            # If the root's value is not between the left boundary (lB) and the right boundary (rB)
            # then the binary search tree is not valid; return False
            if not (root.val > lB and root.val < rB): return False

            # If searching the left child, update the right boundary,
            # because the entire subtree must be less than the current node's value

            # If searching the right child, update the left boundary,
            # because the entire subtree must be greater than the current node's value
            return valid(lB,root.val,root.left) and valid(root.val,rB,root.right)

        # Initially, there are no boundaries, so assign the largest values possible
        return valid(float("-inf"),float("inf"),root)
```
