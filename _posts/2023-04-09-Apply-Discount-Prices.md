---
title: Coding Question - Apply Discount to Prices
date: 2023-00-00 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, string]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/apply-discount-to-prices/description/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
ABC...

**What Went Wrong**  
XYZ...

**What I Learned**  
I LEARNED...

**How I Can Improve**  
I CAN...

**Comments**  
COMMENTS

# Solution Statistics  

**Time Spent Coding**  
17 minutes

**Time Complexity**  
O(n<sup>2</sup>) - This implementation nests a O(n + n) operation inside of a O(n) operation which means in the worst case we would have an O(n * 2n) runtime, which simplifies to O(n<sup>2</sup>), because we ignore constant multiples of n.

**Space Complexity**  
O(1) - Two new variables are created and do not depend on the length of the passed in sentence, resulting in the O(1) space complexity.

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
                # in a try and accept block, if any error is met then continue
                try:
                    # Check for constraint 2
                    # If the number has more than 10 digits, then continue
                    # We must convert it into an integer and then a string because of how
                    # very large numbers are represented
                    # Ex. 1e9 = 1,000,000,000
                    if len(str(int(num[1:]))) > 10: continue       # O(n + n)

                    # Compute the discounted price
                    num = float(num[1:])            # O(n)
                    num -= (num * discount/100)     # O(1)

                    # Place the new price in the sentence
                    sentence[i] = f"${num:.2f}"     # O(1)
                except:
                    continue

        # Join the sentence back together, seperate each element by a space
        return " ".join(sentence)
```
