---
title: Toeplitz Matrix
date: 2023-07-08 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, matrix]
---

### View *Toeplitz Matrix* on [LeetCode](https://leetcode.com/problems/toeplitz-matrix/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n * m) - Every cell in the matrix must be seen, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(1) - No variables are declared, resulting in the O(1) space complexity.

**Runtime Beats**  
95.80% of other submissions  

**Memory Beats**  
93.36% of other sumbissions  

## Explanation  
The algorithm traverses the matrix cell by cell, so the loop only iterates over diagonals with more than one element, allowing for the algorithm to look ahead at the next element in the diagonal. Doing this for every element allows the verification of the Toeplitz Matrix.

## Solution  

```python
class Solution:
    def isToeplitzMatrix(self, matrix: List[List[int]]) -> bool:
        for i in range(len(matrix)-1):
            for j in range(len(matrix[0])-1):
                if matrix[i][j] != matrix[i + 1][j + 1]:
                    return False
        return True
```