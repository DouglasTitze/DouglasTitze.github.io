---
title: Max Area of Island
date: 2023-07-19 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, depth-first search, matrix]
---

### View *Max Area of Island* on [LeetCode](https://leetcode.com/problems/max-area-of-island/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n * m) - Every cell in the matrix must be visited at least once, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - Assuming every cell in the matrix is `1`, there could be n * m recursive calls active simultaneously, resulting in the O(n * m) space complexity.

**Runtime Beats**  
98.32% of other submissions  

## Explanation  
The algorithm explores all non-diagonal directions from every found island and returns the sum of its area. During the exploration of an island, it is "sunk" by being changed to 0 to eliminate repetition of the island.

The algorithm uses depth-first search by fully exploring all directions from the first island until no further islands can be explored. When this condition is met, the sum of islands is sent backward through all the recursive calls to be compared to the current `max_area` finally.

## Algorithm Used  

**Depth-First Search -** An algorithm for traversing a tree/matrix data structure. 
The algorithm begins at the root and searches until it can not continue any deeper. 
Once at the deepest point, the algorithm works backward until all the nodes/cells have been visited. 

## Solution  

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        max_r = len(grid)
        max_c = len(grid[0])
        max_area = 0
        directions = ((1,0),(-1,0),(0,1),(0,-1))

        def explore(r,c):
            # Sink the island
            grid[r][c] = 0

            cur_area = 0
            for x,y in directions:
                new_c = c + x
                new_r = r + y

                # Ensure the next island is valid
                if new_c < 0 or new_c >= max_c: continue
                if new_r < 0 or new_r >= max_r: continue
                if grid[new_r][new_c] == 0: continue
    
                # Increase the area and explore another connected island
                cur_area += explore(new_r,new_c) + 1

            return cur_area

        
        for i in range(max_r):
            for j in range(max_c):
                if grid[i][j] == 1:
                    
                    # Explore all attached islands and update max_area
                    max_area = max(max_area,explore(i,j)+1) 



        return max_area
```