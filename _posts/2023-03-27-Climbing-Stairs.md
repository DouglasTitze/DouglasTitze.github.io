---
title: Climbing Stairs
date: 2023-03-27 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math, dynamic programming, memoization]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/climbing-stairs/){:target="\_blank"} on LeetCode

# My Thoughts  

**What Went Well**  
I immediately realized that I had to be looking for a pattern and had to cache/track the results of each iteration. 

**What Went Wrong**  
Dealing with the first two cases was challenging, and a bug threw off the results by 1 or 2 for each computation. 
I had to submit eight incorrect answers before the pattern stuck out. 
When focusing solely on the correlation between n and its result, I overlooked the correlation between the results.

**What I Learned**  
I refreshed my memory on the definition of memoization. 

**How I Can Improve**  
In the future, I recognize the importance of reading the constraints first and will prioritize this in future problems. 

**Comments**  
Reviewing my previous solution from August, I noticed that using an array significantly improved the runtime. 
However, it's important to note that LeetCode's statistics are inconsistent, and submitting the same answer multiple times may result in significantly different solution statistics for the exact same submission.  
If you'd like to laugh check out this [submission](https://leetcode.com/problems/climbing-stairs/solutions/3302571/fastest-possible-solution-c-professors-hate-him/){:target="_blank"}.

# Algorithm Description

**Memoization -** An optimization technique that makes solutions faster by storing results of previous implementations and recalling that information when the same computation is encountered.

# Solution Statistics  

**Time Spent Coding**  
13 minutes

**Time Complexity**  
O(n) - We must iterate from 3 to n, and since n could be a **large number** the resulting time complexity is O(n).

**Space Complexity**  
O(n) - We must store n values in the cache, resulting in the O(n) space complexity.

**Runtime Beats**  
80.43% of other submissions  

**Memory Beats**  
45.87% of other sumbissions  

# Solution  

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        cache = {1:1,
                 2:2}

        # First two solutions are already in the cache. Start at the third computation
        # Cache is indexed starting a 1, so we must iterate from 3 to n+1
        for i in range(3,n+1):
            # Each iteration is the sum of the two previous solutions (i-1 and i-2)
            cache[i] = cache[i-1] + cache[i-2]

        return cache[n]
```

# Previous Solution

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        ar = [1,2]

        # First two solutions are already in the cache. Start at the third computation
        # Array is indexed starting a 0, so we must iterate from 2 to n
        for i in range(2,n):
            ar.append(ar[i-1] + ar[i-2])

        return ar[n-1]
```
