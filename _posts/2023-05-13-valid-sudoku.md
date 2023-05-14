---
title: Valid Sudoku
date: 2023-05-13 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, hash table, matrix]
---


### View *Valid Sudoku* on [LeetCode](https://leetcode.com/problems/valid-sudoku/){:target="_blank"}

# Solution  

```python
class Solution:
    def isValidSudoku(self, board):
        s = set()

        for r in range(9):
            for c in range(9):
                num = board[r][c]
                if num == ".": continue
                
                check = f"{num} in row # {r}"
                if check in s: return False
                s.add(check)

                check = f"{num} in column # {c}"
                if check in s: return False
                s.add(check)

                check = f"{num} in box @ {[r//3,c//3]}"
                if check in s: return False
                s.add(check)
                
        return True
                
```

# Solution Statistics  

**Time Spent Coding**  
30 minutes

**Time Complexity**  
O(n * m) - We must check each cell, meaning we must iterate through each row (n) and each column (m), resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - We store three unique identifiers for each cell, resulting in the O(n * m) space complexity.  

The space complexity is not O(n * m * 3) because the increase in space remains quadratic despite the multiplier. 
Hence, it is not included in the final space complexity. 

# How It Works
We iterate through each row, while inside each row, we iterate through each cell.  
At each cell, we place the number at that cell into a variable and check if it is a number or an empty space.  
* If it is an empty space, we will `continue` to the next cell.  

If it is a number, place it into three unique string identifiers, one for denoting it and its row, column, and box placements.  
* If this unique identifier is already within the set, we know this is an invalid sodoku board, so we return `False`.  

If this unique identifier is not within the set, then add it.  
If we exit both for loops and have not returned `False`, the sodoku board must be valid.