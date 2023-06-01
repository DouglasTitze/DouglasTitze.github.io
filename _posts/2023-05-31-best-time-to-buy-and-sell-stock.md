---
title: Best Time to Buy and Sell Stock
date: 2023-05-31 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, array, math]
---

### View *Best Time to Buy and Sell Stock* on [LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(n) - Each element in `prices` is only visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

**Runtime Beats**  
99.72% of other submissions  

**Memory Beats**  
37.33% of other sumbissions  

## Explanation
Before iterating through the prices, we must initialize `buy,` `sell,` and `profit.` `buy` and `sell` are set to values they will never exceed to allow for our program to function properly, and `profit` is set to 0.

We now iterate through each price `p` in prices.
*   If the price is less than our current buy price, we must reset our `buy` and `sell` variables to the current price. This is similar to setting our `buy` and `sell` variables to values they will never exceed, allowing us to essentially "reset" our variables to a state where our program will function properly.
*   If the price exceeds our current sell price, we set `sell` equal to it and update the profit to the maximum price, either the difference between the sell and buy or the previous profit.
*   If none of these conditions are satisfied, do nothing

Once all elements in `p` have been visited, we exit the for loop and `return profit.`

## Solution  

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        buy,sell = inf,-inf
        
        profit = 0
        for p in prices:
            if p < buy:
                buy = sell = p
            elif p > sell:
                sell = p
                profit = max(profit, sell - buy)

        return profit
```