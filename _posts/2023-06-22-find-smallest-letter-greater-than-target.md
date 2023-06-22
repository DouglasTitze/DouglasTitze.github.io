---
title: Find Smallest Letter Greater Than Target
date: 2023-06-22 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, binary search]
---

### View *Find Smallest Letter Greater Than Target* on [LeetCode](https://leetcode.com/problems/find-smallest-letter-greater-than-target/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(log n) - Binary search is the main algorithm used in the solution, resulting in the O(log n) time complexity.

**Space Complexity**  
O(1) - The number of created variables is independent of the input, resulting in the O(1) space complexity.

**Runtime Beats**  
98.83% of other submissions  

## Explanation  
The function first checks if there are letters within the input lists which meet our criteria; if none do, then return the first letter, as specified in the problem.

Initialize the left and right pointers and then loop until `l` is greater than `r.` In this modification of binary search, we include where `l` == `r` because of the specific input domain.

Create and initialize `m` to the middle of `l` and `r,` and then check conditionals:
*   `if  target >= letters[m]:` If the target is greater than or equal to the current letter, then there will be smaller letters to the left of the list
*   `else:` If the target is less than the current letter, there will be larger letters to the right of the list

Once the while loop exists, the left pointer will remain at the next greatest letter, so we return the letter at that index.

## Algorithm Used

**Binary Search -** A search algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

## Solution  

```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        if target >= letters[-1] or target < letters[0]:
            return letters[0]

        l = 0
        r = len(letters) - 1

        while l <= r:
            m = (l+r)//2

            if  target >= letters[m]:
                l = m+1
            
            else:
                r = m-1
                
        return letters[l]
```