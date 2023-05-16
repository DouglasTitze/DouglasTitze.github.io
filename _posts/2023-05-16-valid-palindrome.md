---
title: Valid Palindrome
date: 2023-05-16 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, two pointer, string]
---


### View *Valid Palindrome* on [LeetCode](https://leetcode.com/problems/valid-palindrome/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n) - Each element in the string (n) is visited only once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

## Explanation
Before we begin iterating through the string, we must initialize our "pointers," `left` and `right.` We will set both of these variables to their respective values.

We will iterate through the input string as long as the `left` pointer is less than the `right` pointer, ensuring we do not iterate over the same element twice.

We then check if the character at each pointer is alphabetical or numeric; if neither, we will increment or decrement the respective pointer toward the other and `continue` to the next iteration of the loop. If we exclude the `continue`, we could increment/decrement one of the pointers to a non-alphanumeric character and cause an error.

We then perform the `.lower()` function on each character to convert them to lowercase because the problem considers uppercase and lowercase characters equal. Once converted, the program will check if they are identical; if not, we return `False` since the string no longer meets the criteria to be a palindrome.

If all conditions pass, and the code does not exit the while loop or go to the next iteration, we increment both pointers inwards.

If the while loop exits, the string is verified to be a palindrome, and we return `True`.

# Algorithm Description

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be if the elements are equal, and if they are not, we should exit because that violates our search criteria.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view  

## Solution  

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        left = 0
        right = len(s) - 1

        while left < right:
            if s[left].isalnum() == False: 
                left += 1 
                continue
                
            if s[right].isalnum() == False: 
                right -= 1
                continue
                
            if s[left].lower() != s[right].lower(): return False

            left += 1
            right -= 1

        return True
```