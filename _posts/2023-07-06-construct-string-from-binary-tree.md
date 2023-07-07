---
title: Construct String from Binary Tree
date: 2023-07-06 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string, binary tree]
---

### View *Construct String from Binary Tree* on [LeetCode](https://leetcode.com/problems/construct-string-from-binary-tree/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - Every node and its children are visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - The output string has a factor of n elements, that factor is ignored since it is a constant and does not affect the growth rate, resulting in the O(n) space complexity.

**Runtime Beats**  
99.72% of other submissions  

**Memory Beats**  
86.19% of other sumbissions  

## Explanation  
All calls of `tree2str` will be on a node that is not equal to null, so the algorithm stores its value and left and right children.

1.  `if left or right:` If one or more children are not equal to None, then the algorithm continues.  
2.  `if left and right:` If there are two children, recursively call `tree2str` and add it to the output string in the proper format  
3.  `elif right:` If there is only a right node, recursively call `tree2str` and add it to the output string in the proper format. Since there is no left node, it adds an empty parenthesis to accurately represent an empty left node as a string.  
4.  `else`: If there is only a left node, recursively call `tree2str` and add it to the output string in the proper format.  

Finally, exit the if statements, and return the final output string.  

## Data Structure Used   

**Binary Tree -** A rooted tree where every node has at most two children, the left and right children.  

## Solution  

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def tree2str(self, root: Optional[TreeNode]) -> str:
        string = str(root.val)
        left = root.left
        right = root.right

        if left or right:
            if left and right:
                string += "(" + self.tree2str(left) + ")"
                string += "(" + self.tree2str(right) + ")"

            elif right:
                string += "()" + "(" + self.tree2str(right) + ")"

            else:
                string += "(" + self.tree2str(left) + ")"
                
        return string
```