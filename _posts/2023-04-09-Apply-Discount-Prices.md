---
title: Coding Question - Apply Discount to Prices
date: 2023-04-09 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, string]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/apply-discount-to-prices/description/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
Despite having issues with edge cases, I completed this question in a reasonable amount of time.

**What Went Wrong**  
While attempting to solve this question, I tried googling for operations to simplify my solution but came up empty-handed. 
Fortunately, I was able to implement it without the help of external resources.

**What I Learned**  
I refreshed my memory on string formatting for decimal numbers.

**How I Can Improve**  
I can continue to practice using built-in functions and review other submissions to gain a new perspective on how to approach this problem.

**Comments**  
This challenge was fun, but it had cheap edge cases and unnecessarily dirty data, but overall a nice problem to practice lots of essential coding concepts and built-in functions.

# Solution Statistics  

**Time Spent Coding**  
17 minutes

**Time Complexity**  
O(n<sup>2</sup>) - This implementation nests an O(n + n) operation inside of an O(n) operation, which means in the worst case, we would have an O(n * 2n) runtime, which simplifies to O(n<sup>2</sup>) because we ignore multiples of n.

**Space Complexity**  
O(1) - Two new variables are created and do not depend on the length of the sentence, resulting in the O(1) space complexity.

**Runtime Beats**  
67.50% of other submissions  

**Memory Beats**  
84.88% of other sumbissions  

# Solution  

```python
class Solution:
    def discountPrices(self, sentence: str, discount: int) -> str:
        # Seperate the sentence by spaces into an array
        sentence = sentence.split()         # O(n)

        # Iterate through each word/phrase in the sentence
        for i in range(len(sentence)):      # O(n)
            num = sentence[i]               # O(1)

            # Check for constraint 1
            if num[0] == "$":               # O(1)
                # Lots of edge cases can be solved simply by placing the following
                # in a try-and-accept block, if any error is met, then continue
                try:
                    # Check for constraint 2
                    # If the number has more than ten digits, then continue
                    # We must convert it into an integer and then a string because of how
                    # very large numbers are represented
                    # Ex. 1e9 = 1,000,000,000
                    if len(str(int(num[1:]))) > 10: continue       # O(n + n)

                    # Compute the discounted price
                    num = float(num[1:])            # O(n)
                    num -= (num * discount/100)     # O(1)

                    # Repace the price in the sentence with the new one
                    # The ":.2f" format makes sure that there is always two decimal
                    # points of accuracy included when converted into a string
                    sentence[i] = f"${num:.2f}"     # O(1)
                except:
                    continue

        # Join the sentence back together, separate each element by a space
        return " ".join(sentence)
```

