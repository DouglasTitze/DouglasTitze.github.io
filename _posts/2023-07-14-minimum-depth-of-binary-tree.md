---
title: Minimum Depth of Binary Tree
date: 2023-07-14 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, binary tree, depth-first search]
---

### View *Minimum Depth of Binary Tree* on [LeetCode](https://leetcode.com/problems/minimum-depth-of-binary-tree/){:target="_blank"}  

## Statistics  

**Time Spent Coding**    
15 minutes

**Time Complexity**  
O(n) - Each node in the tree must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The number of recursive calls is at most n and will be stored in the memory stack, resulting in the O(n) space complexity.

**Memory Beats**  
54.32% of other sumbissions  

## Explanation  
The algorithm explores all paths and returns the path with the minimum length by checking both children and recursively calling the minDepth method on them.

If the node is none, then return 0.

If a leaf is found, the algorithm terminates the recursive calls and returns 1.

If a leaf is not found, it returns the lowest of the children's recursive calls.

# Algorithm and Data Structure Used

**Depth-First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.  

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
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if root == None: return 0

        l = root.left
        r = root.right

        # Leaf found
        if l == None and r == None:
            return 1
        
        else:
            lowest = float(inf)

            if l:
                lowest = min(lowest,self.minDepth(l))
                
            if r:
                lowest = min(lowest,self.minDepth(r))

            return lowest + 1
```