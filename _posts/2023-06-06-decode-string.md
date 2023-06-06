---
title: Decode String
date: 2023-06-06 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, string, stack]
---

### View *Decode String* on [LeetCode](https://leetcode.com/problems/decode-string/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(?) - The time complexity strictly depends on the number of encoded strings and the number of times they are repeated, making it impossible to predict the time complexity.

**Space Complexity**  
O(?) - The space complexity strictly depends on the number of encoded strings and the number of times they are repeated, making it impossible to predict the space complexity.

## Explanation
The algorithm works in two sections, adding to the stack and converting the stack into a decoded string.
Before beginning the logic, the stack must be declared.

The algorithm iterates through each character `c` in the input string `s.`

*  If the current character is NOT a closing bracket ( ] ), add `c` to the stack
*  If the character is a closing bracket, convert the stack into a decoded string.

To begin this process, extracts all the characters and place them into our substring `substrate.` To ensure the characters are placed in `substr` in their correct order, the string manipulation must be performed like `substr = stack.pop() + substr` and not `substr += stack.pop` as this will result in the `substr` being in reverse order.

After this, remove the opening bracket from the stack to avoid incorrect substrings or unexpected behavior.

Now declare `k`. It eventually contains a string representation of the number of times the substring will repeat. Again the manipulation of `k` must be performed similarly to the creation of `substrate.` Except for the iteration through the sting is different, the conditions that are being checked are: if the stack is non-empty, to avoid incrementing and poping beyond the elements in the list, and if the last character, which will be poped, is a number.

Once all steps are completed, append `substr` `k` times to the stack, but to do this, `k` must first be converted into an integer `int()`.

Once all characters have been iterated through, join each element in the list separated by no white space, and return it.

## Data Structure Used

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack. A stack follows the first in, last out, or FILO theme.

Since Python already has O(1) push (append) and pop (pop) operations, no libraries are needed.

**Visual Examples**
Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view

## Solution  

```python
class Solution:
    def decodeString(self, s: str) -> str:
        stack = []

        for c in s:
            # Add characters not equal to ']' to the stack
            if c != ']':
                stack.append(c)

            else:
                # Create substring to be multiplied
                substr = ''
                while stack[-1] != '[':
                    # Do not use +=
                    substr = stack.pop() + substr

                # Remove the open bracket ([)
                stack.pop()

                # Create a string representation of  k
                k = ''
                while stack and stack[-1].isdigit():
                    # Do not use +=
                    k = stack.pop() + k

                # Multiply the substring k times and then append it to the stack
                stack.append(substr * int(k))

        return ''.join(stack)
```