---
title: Binary Tree Level Order Traversal
date: 2023-04-12 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [binary tree, depth first search, breadth first search]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/binary-tree-level-order-traversal/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I implemented my solution quickly and had a very good runtime, and after optimizing, I got an outstanding space complexity.

**What I Learned**  
I learned how to convert my program into a more optimal solution using the breadth-first search algorithm.

**How I Can Improve**  
By practicing the implementation of depth and breadth-first search, I can master two very commonly used algorithms for trees and graphs.

# Algorithm Description

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited.

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
It creates a deque of elements yet to be visited and then iterates through each level (similar properties) until there are no more elements to iterate through. In this example, the similar property would be equal depths in the tree. 

The proper definition for breadth-first search when not being applied to this specific problem can be found [here](https://en.wikipedia.org/wiki/Breadth-first_search){:target="_blank"}.

**Visual Examples**  
Binary Tree, [click](https://cdn.programiz.com/sites/tutorial2program/files/perfect-binary-tree_0.png){:target="_blank"} to view 

Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics For Depth First Search

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - Each node (n) must call the search function, and the search function is an O(1) time complexity function, resulting in the O(n) space complexity.

**Space Complexity**  
O(n) - Each node must be stored in the sorted list, resulting in the O(n) space complexity. 
Truly the space complexity is O(n + log n). 
The log n is for the most amount of possible recursive calls yet to be completed.

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
        if root is None: return []  # O(1)

        self.order = []     # O(1)

        def search(root,depth):
            
            # If the length of the ordered list is equal to the depth,
            # then that depth has not been visited yet, so append it
            # with the given element
            if len(self.order) == depth:    # O(1)
                self.order.append([root.val])   # O(1)

            # If the length != the length, then append the current element
            # to the index of the depth
            else:
                self.order[depth].append(root.val)  # O(1)

            # Only call the search function if the node != None
            if root.left: search(root.left,depth+1)     # O(1)
            if root.right: search(root.right,depth+1)   # O(1)

        Search(root,0)  # O(n)
        return self.order
```

# Solution Statistics For Breadth-First Search

**Time Spent Optimizing**  
5 minutes

**Time Complexity**  
O(n) - Each node (n) must pass through the while loop, and since the while loop is an O(1) block of code, we get an O(n) time complexity.

**Space Complexity**  
O(n) - We are constantly pushing and popping off the deque but only appending to the sorted list. The number of elements in the sorted list exceeds that of the deque, resulting in the O(n) space complexity.

**Runtime Beats**  
89.74% of other submissions  

**Memory Beats**  
97.74% of other sumbissions  

# Optimal Solution  

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if root is None: return []  # O(1)

        order = []  # O(1)
        q = deque() # O(1)
        q.append((root,0))  # O(1)

	# Continuously iterate through the deque until it is empty
        while q:
            cur, depth = q.popleft()    # O(1)
            
            if depth == len(order):     # O(1)
                order.append([cur.val]) # O(1)
            else:
                order[depth].append(cur.val)    # O(1)

            if cur.left: q.append((cur.left,depth+1))   # O(1)
            if cur.right: q.append((cur.right,depth+1)) # O(1)
        
        return order
```