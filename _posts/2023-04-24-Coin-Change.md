---
title: Coin Change
date: 2023-04-24 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array, dynamic programming, depth-first search]
---

# Links  

Go to the [solution](#solution)  
Go to the [question](https://leetcode.com/problems/coin-change/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew the solution could not utilize a greedy algorithm, and we had to cache our result for each iteration.

**What I Learned**  
I learned how to apply breadth-first search in a unique way and gained more experience with dynamic programming.

**How I Can Improve**  
All I can keep doing is practicing. 
Knowing dynamic programming is one of the more difficult concepts in computer science is making me keep my hopes up, but I am sad that I could not create a working solution on my own.

# Algorithm Description

**Depth First Search -** An algorithm for traversing data structures.
The algorithm begins at the root node and searches until it can not continue any deeper.
Once at the deepest point, the algorithm works backward until all the nodes have been visited.  

In this problem, our root node would be the curAmount, and our code works backward inside of our ``` if curAmount-coin >= 0: ``` statement by reassigning the curAmount value in our dp.

# Solution Statistics  

**Time Complexity**  
O(n * m) - We are taking the amount to be n and the length of coins to be m.
We must iterate through each element in our dp array from 0 to n +1, and for each iteration, we must iterate through each element in m, resulting in the O(n + 2 * m) time complexity. 
Since big O ignores constants, O(n * m) is the proper time complexity.

**Space Complexity**  
O(n) - Our dp array stores n elements equivalent to the input integer amount + 1. 
Since big O ignores constants, it results in an O(n) space complexity.

**Runtime Beats**  
41.57% of other submissions  

**Memory Beats**  
81.31% of other sumbissions  

# Solution  

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        # This array will store the least amount of coins it takes to 
        # reach the current index (aka "curAmount")
        # Assign each element from 0 to amount + 1 an impossible value (inf)
        dp = [inf] * (amount + 1)
        # Initialize 0 to 0
        dp[0] = 0

        for curAmount in range(1,amount + 1):
            for coin in coins:
                if curAmount-coin >= 0:
                    # Check if the number of coins to compute curAmount
                    # is smaller than 1 + num coins to compute curAmount - coin
                    dp[curAmount] = min(dp[curAmount], 1 + dp[curAmount - coin])

        # If the minimum number of coins to get amount is unable to be computed, 
        # then the element at index amount will have remained as the impossible value; return -1
        if dp[amount] == inf: return -1

        return dp[amount]
```
