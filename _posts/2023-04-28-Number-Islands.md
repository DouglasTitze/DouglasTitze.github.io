---
title: Number of Islands
date: 2023-04-28 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, depth-first search, matrix, array]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/number-of-islands/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I recognized that I needed to use depth-first search and how to approach the problem.

**What I Learned**  
I got more practice with matrix traversal and depth-first search.

**Comments**  
The solution statistics for my submission were far from a solution identical to mine, except for variable names. 
So again, take the solution statistics with a grain of salt.

# Algorithm Description

**Depth First Search -** An algorithm for traversing a tree data structure. 
The algorithm begins at the root node and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes have been visited. 

In this problem, the root node can be thought of as an element with the value of "1, " and the "deepest" point will be a "0".

**Visual Examples**  
Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n * m) - We are taking the number of rows to be n and the number of columns to be m. 
Since we must iterate through each element, it results in an O(n * m) time complexity. 
We also may iterate through each element a second time if the entire grid is "1"s, so technically, we have an O(2 * n * m) time complexity. 
But big O ignores constant multiples of n and m, resulting in the O(n * m) time complexity. 

**Space Complexity**  
O(1) - Only three new variables are created, and the number of created variables does not depend on n or m, resulting in the O(1) space complexity.  

**Runtime Beats**  
56.70% of other submissions  

**Memory Beats**  
39.16% of other sumbissions  

# Solution  

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        islands = 0
        self.maxR = len(grid)
        self.maxC = len(grid[0])

        def depth(r,c):

            # Check if the indices are within the gird
            if r >= self.maxR or r < 0: return False
            if c >= self.maxC or c < 0: return False 

            # Check if the cell contains a "1."
            if grid[r][c] != '1': return False

            # Change to 0
            grid[r][c] = 0

            # Explore all adjacent indices
            depth(r+1,c)
            depth(r-1,c)
            depth(r,c+1)
            depth(r,c-1)
                

        for r in range(self.maxR):
            for c in range(self.maxC):
                
                # If the cell contains "1," explore its adjacent indices
                if grid[r][c] == "1":

                    # Only increment islands within this statement this
                    # satisfied the "return the number of islands" condition.

                    # If there is land attached to this island
                    # depth will remove all of it from the grid, allowing for
                    # proper incrementation of islands.
                    islands += 1
                    depth(r,c)

        return islands
```
