---
title: Brick Wall
date: 2023-06-23 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, hash map]
---

### View *Brick Wall* on [LeetCode](https://leetcode.com/problems/brick-wall/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n * m) - The algorithm traverses through every element, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n * m) - In the worst case, there are no gaps with a frequency greater than one resulting in the dictionary containing about n * m elements.

**Runtime Beats**  
81.85% of other submissions  

## Explanation  
The algorithm records the frequency of a gap at a certain number in the `count_gap` dictionary and subtracts that from the length of the wall (the total amount of layers).

The algorithm calculates the gaps by taking the sum of the current brick and its previous bricks; it then increments the frequency of this gap in the dictionary. The algorithm avoids summing the last element of each row because that would result in an incorrect output since the last element of each row will always sum to the same number due to it being the endpoint of the brick wall.

Once the algorithm records all the gaps, it subtracts the gap with the highest frequency from the total amount of layers resulting in the least amount of bricks to go through.

## Data Structure Used

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.


## Solution  

```python
class Solution:
    def leastBricks(self, wall: List[List[int]]) -> int:
        count_gap = {0 : 0}

        for row in wall:
            total = 0

            for brick in row[:-1]:
                total += brick

                count_gap[total] = 1 + count_gap.get(total, 0)

        return len(wall) - max(count_gap.values())
```