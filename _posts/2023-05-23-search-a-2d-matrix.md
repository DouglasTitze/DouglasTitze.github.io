---
title: Search a 2D Matrix
date: 2023-05-23 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search, matrix]
---


### View *Search a 2D Matrix* on [LeetCode](https://leetcode.com/problems/search-a-2d-matrix/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(log (m * n)) - We are performing binary search on a sorted matrix with m rows where each row contains n elements, resulting in the O(log (m * n)) time complexity.

**Space Complexity**  
O(1) - The number of variables is independent of m and n, resulting in the O(1) space complexity.

## Explanation
This problem can be broken into two parts, performing a binary search to identify the row the target may be in and performing a binary search on that row.

We must initialize our top and bottom pointers to their respective values. 

We then begin iterating until our top pointer is greater or equal to our bottom, or we break out of the loop. 
We initialize our `row` variable with the middle index between the top and bottom with the formula `(bot+top)//2` and then check the values at that row.
*   If the value at the last index of the row is less than the target, we must increment the top pointer to look for larger values.
*   Similarly, if the value at the first index of the row is greater than the target, we must decrement the bottom pointer to look for smaller values.
*   If neither of these conditions are met, we may have identified the row where the target is.

To ensure our selected row is valid, we must check if the top pointer is greater than the bottom and if it returns False.

Since our `row` variable was nested within the `while` loop, we must redeclare it. We also must declare our left and right pointers to their respective values.

We then begin iterating until our left (`l`) pointer is greater or equal to our right (`r`) pointer. We initialize our `mid` pointer to the index between our left and right pointers. 
Like the previous while loop, we will check if the row and middle index's value equals the target, is less than, or is greater than, and adjust our pointers accordingly. 
If the target is found, we `return True`; if it is not, then the while loop will eventually exit.

We will `return False` if the while loops exit because this means the target was not found in its expected row.

## Algorithm Description

**Binary Search -** A search algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        top,bot = 0, len(matrix)-1
        while top <= bot:
            row = (bot+top)//2
            if matrix[row][-1] < target:
                top = row + 1
            elif matrix[row][0] > target:
                bot = row -1
            else: break
        
        if top > bot: return False

        row = (bot+top)//2
        l,r = 0, len(matrix[0])-1
        while l <= r:
            mid = (l+r)//2
            if matrix[row][mid] == target:
                return True
            elif matrix[row][mid] < target:
                l = mid+1
            else:
                r = mid-1

        return False
```