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
I learned how to convert my program into a more optimal solution using the breadth first search algorithm.

**How I Can Improve**  
Practice the implementation of both depth and breadth first search and become proficient in both.

**Comments**  
COMMENTS

# Algorithm Description

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited.

**Breadth-first search -** A graph/matrix traversal algorithm that searches for elements with a given property. 
It creates a deque of elements yet to be visited and then iterates through each level (similar elements) until there are no more elements to iterate through.

The proper definition for breadth-first search when not being applied to this specific problem can be found [here](https://en.wikipedia.org/wiki/Breadth-first_search){:target="_blank"}.

**Visual Examples**  
Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view 

Depth first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics For Depth First Search

**Time Spent Coding**  
15 minutes

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

# Solution Statistics For Depth First Search

**Time Complexity**  
O(x) - xxxxx, resulting in the O(n) space complexity.

**Space Complexity**  
O(x) - xxxx, resulting in the O(n) space complexity.

**Runtime Beats**  
xxxx% of other submissions  

**Memory Beats**  
xxxx% of other sumbissions  

# Solution  

```python
```
