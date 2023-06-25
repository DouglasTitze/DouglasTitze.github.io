---
title: Keyboard Row
date: 2023-06-25 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, string, hash table]
---

### View *Keyboard Row* on [LeetCode](https://leetcode.com/problems/keyboard-row/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n * m) - We must iterate through every word in the input list (n) and then iterate through every character of each word (m), resulting in the O(n * m) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the input list and number of characters per word, resulting in the O(1) space complexity.

**Runtime Beats**  
96.47% of other submissions  

**Memory Beats**  
94.31% of other sumbissions  

## Explanation  
Before iteration, create three hash tables, each representing a row in the keyboard and a result array to store the output.

Begin iterating through each word in the input list and convert it to lowercase.

Check if the word's first letter is in a row; if it is, then continue and check if all of its characters are also in that row; if true, then append that word to the result list.

Once the word list has been iterated, return the result.

## Data Structure Used

**Hash Table (Set) -** An unordered container of non-repeating values.  

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  


## Solution  

```python
class Solution:
    def findWords(self, words: List[str]) -> List[str]:
        r1 = set('qwertyuiop')
        r2 = set('asdfghjkl')
        r3 = set('zxcvbnm')

        result = []

        for word in words:
            lower_word = word.lower()

            if lower_word[0] in r1 and all(c in r1 for c in lower_word):
                result.append(word)
            elif lower_word[0] in r2 and all(c in r2 for c in lower_word):
                result.append(word)
            elif lower_word[0] in r3 and all(c in r3 for c in lower_word):
                result.append(word)

        return result
```