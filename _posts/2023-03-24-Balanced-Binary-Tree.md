---
title: Balanced Binary Tree
date: 2023-03-24 00:00:00 -400
categories: [Coding Questions, Easy, Search Algorithms]
tags: [python, depth first search, tree]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/balanced-binary-tree/description/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I remembered how to traverse trees and thought of the algorithm I would perform to get the solution quickly.
I remembered the infinity keyword, which allowed me to solve the problem without referring to the documentation.  

**What Went Wrong**  
I implemented the algorithm incorrectly, forgetting to get the largest depth, and instead, I was getting the depth corresponding to the left or right side of the tree.
I also struggled to create a condition that would allow me to realize the height was unbalanced, but eventually, I remembered (inf).  

**What I Learned**  
I refreshed my memory about trees, the depth-first search algorithm, and how to traverse trees.
I need to review all the test cases and constraints before attempting the solution to familiarize myself with the question and allow more time to think of a solution.  

**How I Can Improve**  
I could not think of an exit condition because I was trying to use a value that could be generated from a test case.
If I had reviewed the constraints, I could have started thinking of another way to exit instead of implementing multiple incorrect exit conditions before reviewing the constraints.  

**Comments**  
I could have completed this faster, but I am satisfied with the outcome.
I flowed through the problem and did not run into an error that halted me for more than 2 minutes, so overall, I am happy with today's result.
This is not the most optimal solution, and I could achieve a more optimal solution by exiting the function as soon as a violation of the tree balance occurs.  

# Algorithm Description

**Depth First Search -** An algorithm for traversing a tree data structure.
The algorithm begins at the root node and searches until it can not continue any deeper.
Once at the deepest point, the algorithm works backward until all the nodes have been visited.  
  
The algorithm I chose retrieved the largest depth of each child and then passed those values up to the parent. 
If there ever were a violation of the tree balance, I would set both depths to infinity. This would allow the function to continue running while propagating the violation trigger until the final comparison of depths.  

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Visual Examples**  
Depth first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view

Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view 

# Solution Statistics  

**Time Spent Coding**  
20 minutes  

**Time Complexity**  
O(n) - The getDepth() function must be run on every node in the tree  

**Space Complexity**  
O(n) - A left and right variable is created for each call of getDepth()  

**Runtime Beats**  
84.89% of other submissions  

**Memory Beats**  
85.16% of other sumbissions  

# Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        # Define the reccursive function
        def getDepth(root) -> [int, int]:
            if root == None:
                return 0,0

            left = 0
            right = 0

            if root.left:
                # Get the largest value of the two children and increment by 1
                left = max(getDepth(root.left)) + 1     
            if root.right:
                # Get the largest value of the two children and increment by 1
                right = max(getDepth(root.right)) + 1   

            # Check if the values differ by more than 1, if this is true then the tree's balance has been violated
            if abs(left-right) > 1:                     
                left = inf
                right = inf 

            return [left, right]

        # Begin depth first search starting at the root node
        left, right = getDepth(root)                    
        
        # Check if the values differ by less than 2, if this is true then the tree's balance has not been violated
        if abs(left-right) < 2:                         
            return False
        
        return True
```
