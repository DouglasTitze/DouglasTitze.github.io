---
title: Jewels and Stones
date: 2023-04-05 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/jewels-and-stones/){:target="_blank"} on LeetCode  

**What I Learned**  
I learned how to document time complexities involving more than one array appropriately.

**Comments**  
Again LeetCode's statistics are inconsistent.
According to LeetCode, the desired solution includes a dictionary which would be more efficient if larger inputs were tested.

# Solution Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n * m) - For each element in jewels (n), we traverse each element in stones (m), resulting in the O(n * m) time complexity.

**Space Complexity**  
O(1) - Only one new variable is created, and the number of variables declared does not depend on the number of elements in the string, resulting in the O(1) space complexity.

**Runtime Beats**  
99.99% of other submissions  

**Memory Beats**  
99.99% of other sumbissions  

# Solution  

```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        num_jewels = 0
        
        for jewel in jewels: # O(n)
            num_jewels += stones.count(jewel) # O(m)

        return num_jewels
```