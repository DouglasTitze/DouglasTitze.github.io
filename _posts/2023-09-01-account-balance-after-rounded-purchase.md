---
title: Account Balance After Rounded Purchase
date: 2023-09-01 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, math]
---

### View *Account Balance After Rounded Purchase* on [LeetCode](https://leetcode.com/problems/account-balance-after-rounded-purchase/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(1) - Only simple machine instructions are ran, and no operation iterates through the input, resulting in the O(1) time complexity.

**Space Complexity**  
O(1) - Only one variable is created, resulting in the O(1) space complexity.

**Runtime Beats**  
99.53% of other submissions  

**Memory Beats**  
99.01% of other sumbissions  

## Explanation  
_The comments explain the program and provide examples._

## Solution  

```python
class Solution:
    def accountBalanceAfterPurchase(self, cost: int) -> int:
        # Calculate and store remainder
        r = cost % 10

        # If the remainder is >= to 5, then round up by adding 10,
        # since the remainder is always added to the account
        if r >= 5:
            cost += 10
        
        # Return the account balance after purchase with adjusted price
        return 100 - cost + r

        ''' Examples
        Cost = 9
        Remainder = 9
        Account = 100 + 10 - 9 + 9

        Cost = 17
        Remainder = 7
        Account = 100 + 10 - 17 + 7

        Cost = 14
        Remainder = 4
        Account = 100 - 14 + 4
        '''
```