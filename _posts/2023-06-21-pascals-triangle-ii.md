---
title: Pascal's Triangle II
date: 2023-06-21 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, dynamic programming]
---

### View *Pascal's Triangle II* on [LeetCode](https://leetcode.com/problems/pascals-triangle-ii/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n) - The algorithm iterates from 0 to rowIndex-1, which were are taking to be n, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Again, the algorithm stores rowIndex (n) + 1 elements, and because big-O ignores constants, it results in the O(n) space complexity.

**Runtime Beats**  
90.69% of other submissions  

**Memory Beats**  
64.80% of other sumbissions  

## Explanation  
The algorithm replaces the result `res` with the ith iteration of the Pascals triangle.

It does this by iterating from 0 to `rowIndex,` and each iteration of this loop performs another for a loop.

Inside the for loop, it adds the `j`th element and the j+1th appending each addition from 0 to `i`.

Since each Pascal triangle beyond case 0 starts and ends with a 1, this is built into the for loop to simplify the logic and the inner for loop.

Once the outer for loop exits, return the `res,` which is now equal to the rowIndex of the Pascals triangle.

## Solution  

```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        res = [1]

        for i in range(rowIndex):
            new_res = [1]

            for j in range(i):
                new_res.append(res[j] + res[j+1])

                
            
            new_res.append(1)
            res = new_res
    
        return res
```