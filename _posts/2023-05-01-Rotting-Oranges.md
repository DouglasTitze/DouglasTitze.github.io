---
title: Rotting Oranges
date: 2023-05-01 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, breadth-first search, matrix]
---

# Links  

Go to the [solution](#solution)  
Go to the [question](https://leetcode.com/problems/rotting-oranges/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew a deque was needed to accurately increment the minutes meaning breadth-first search was required.

**What Went Wrong**  
Although I knew breadth-first search was needed, I approached the problem similar to that of a depth-first search, causing many problems.

**What I Learned**  
I learned how to implement a breadth-first search algorithm properly.

**How I Can Improve**  
I can learn more about breadth-first search and how to implement it in more scenarios.

**Comments**  
Solution statistics are excluded from this post because they are inconsistent and inaccurately represent the efficiency of the solution relative to other solutions. 
This is because almost all of the other submissions are very similar to mine, except they have fewer lines of code but are so compact they are illegible. 
A special thank you to the very well-explained answer given by c0deman, which can be viewed [here](https://leetcode.com/problems/rotting-oranges/solutions/563686/python-clean-well-explained-faster-than-90/){:target="_blank"}.

# Algorithm Description

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
It creates a deque of elements yet to be visited and then iterates through each level (similar properties) until there are no more elements to iterate through. 

In this example, a similar property would be the recently added rotten tomatoes. 
Each grouping of rotten tomatoes are the only tomatoes that can cause fresh tomatoes to rot within the same minute.

# Solution Statistics  

**Time Complexity**  
O(n * m) - Each cell in the matrix is visited, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - In the worst scenario, all the tomatoes are rotten, meaning we would add all of them to the deque, resulting in the O(n * m) space complexity.

# Solution  

```python
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        rows = len(grid)
        cols = len(grid[0])
        
        # keep track of fresh oranges
        fresh = 0
        
        # queue with rotten oranges (for BFS)
        rotten = deque()
        
        # visit each cell in the grid
        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 2:
                    # Add the rotten orange coordinates to the queue
                    rotten.append((r, c))

                elif grid[r][c] == 1:
                    # update fresh oranges count
                    fresh += 1
        
        # keep track of minutes passed.
        minutes = 0
        
        # If there are rotten oranges in the queue and there are still fresh oranges in the grid, keep looping
        while rotten and fresh > 0:

            # update the number of minutes passed
            minutes += 1
            
            # process rotten oranges on the current level
            for _ in range(len(rotten)):
                x, y = rotten.popleft()
                
                # visit all the adjacent cells
                for dx, dy in [(1,0), (-1,0), (0,1), (0,-1)]:
                    # calculate the coordinates of the adjacent cell
                    xx, yy = x + dx, y + dy

                    # ignore the cell if it is out of the grid boundary
                    if xx < 0 or xx == rows or yy < 0 or yy == cols:
                        continue

                    # ignore the cell if it is empty '0' or rotten '2'
                    if grid[xx][yy] == 1:                    
                        # update the fresh oranges count
                        fresh -= 1
                        
                        # Mark the current fresh orange as rotten
                        grid[xx][yy] = 2
                        
                        # Add the current rotten to the queue
                        rotten.append((xx, yy))

        
        # return the number of minutes taken to make all the fresh oranges to be rotten
        # return -1 if there are fresh oranges left in the grid (there were no adjacent rotten oranges to make them rotten)
        return minutes if fresh == 0 else -1
```
