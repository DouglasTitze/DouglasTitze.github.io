---
title: Roman to Integer
date: 2023-05-30 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, hash map, string, math]
---


### View *Roman to Integer* on [LeetCode](https://leetcode.com/problems/roman-to-integer/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
7 minutes

**Time Complexity**  
O(n) - We must visit each element in the input string at least once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

**Runtime Beats**  
70.70% of other submissions  

**Memory Beats**  
55.33% of other sumbissions  

## Explanation
Before iterating through the string, we must declare three variables, our dictionary `dic`, which will convert any roman numeral `n` into its corresponding value, `total` to store our running total; and `prev` to store the value at the previous `n.`

We now iterate through each Roman number `n` in our input string `s` and create a new variable `cur` to store the current value at `n.` 
We always add the value of cur to the total, and to correct multiple additions and/or Roman numerals not in the dictionary, we check if the previous number is larger than the current. 
*   If the previous number was smaller, we must remove the previous addition from the total and remove it from the number that was just added to the total; all of this can be done by executing `total -= 2*prev`
*   If the previous number was not smaller, continue to the next line

Once our `if` statement has run, we can replace `prev` with the current value at `n` and continue until the input string has been fully iterated; this will make us exit the `for` loop and `return total.`

# Data Structure Description

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

**Visual Examples**  
Illustration of key value pair mapping, [click](https://www.learnbyexample.org/wp-content/uploads/python/Dictionary-Key-Value-Pairs-Illustration.png){:target="_blank"} to view   

## Solution  

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        dic = { "I":1,
                "V":5,
                "X":10,
                "L":50,
                "C":100,
                "D":500,
                "M":1000 }

        total = 0
        prev = dic[s[0]]

        for n in s:
            cur = dic[n]
            total += cur

            if prev < cur: total -= 2*prev
            
            prev = cur

        return total
```