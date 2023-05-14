---
title: Valid Sudoku
date: 2023-05-13 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, hash table, matrix]
---

### View _Valid Sudoku_ on [LeetCode](https://leetcode.com/problems/valid-sudoku/){:target="\_blank"}

## Statistics

**Time Spent Coding**  
30 minutes  

**Time Complexity**  
O(n * m) - We must check each cell, meaning we must iterate through each row (n) and each column (m), resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - We store three unique identifiers for each cell, resulting in the O(n * m) space complexity.

The space complexity is not O(n * m * 3) because the increase in space remains quadratic despite the multiplier.
Hence, it is not included in the final space complexity.

## Explanation

We iterate through each row, while inside each row, we iterate through each cell.  
At each cell, we place the number at that cell into a variable and check if it is a number or an empty space.

- If it is an empty space, we will `continue` to the next cell.

If it is a number, place it into three unique string identifiers, one for denoting it and its row, column, and box placements. 
The identifier to check if the box of the 3x3 grid is valid, is slightly different than the rest. 
Each box contains 3 rows and 3 columns, meaning each box can be identified by the current rows and columns floor division by 3 `[r//3,c//3]`, this remaineder is equivelent to the box the number is within.

- If this unique identifier is already within the set, we know this is an invalid sodoku board, so we return `False`.

If this unique identifier is not within the set, then add it.  
If we exit both for loops and have not returned `False`, the sodoku board must be valid.

## Solution

```python
class Solution:
    def isValidSudoku(self, board):
        s = set()

        for r in range(9):
            for c in range(9):
                num = board[r][c]
                if num == ".": continue

                # Create row identifier
                check = f"{num} in row # {r}"
                
                # Check identifier
                if check in s: return False
                s.add(check)

                # Create
                check = f"{num} in column # {c}"

                # Check
                if check in s: return False
                s.add(check)

                # Create
                check = f"{num} in box @ {[r//3,c//3]}"

                #Check
                if check in s: return False
                s.add(check)

        return True

```