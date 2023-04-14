---
title: Evaluate Reverse Polish Notation
date: 2023-04-14 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [math, stack, array]
---

# Links  

Go to my [solution](#optimized-solution)  
Go to the [question](https://leetcode.com/problems/evaluate-reverse-polish-notation/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I immediately knew how to implement the solution and optimized my code quickly.

**What Went Wrong**  
I got stuck on one requirement because the floor operation kept returning -1 for some edge cases.

**What I Learned**  
I learned that when the divisor is greater than the dividend and you use the floor operator, it returns -1. 
I also learned that the int() function rounds the input towards 0 and not to the nearest whole number.

**How I Can Improve**  
I could review the documentation for operators and dive into their more fine details, such as above.

**Comments**  
I initially attempted to make my solution smaller by adding the function, but it obviously had the opposite effect. 
Thankfully after looking at the solution statistics, I realized I had to optimize my solution and did so accordingly. 
The optimal solution is much more streamlined and type-safe.

# Data Structure Description

**Stack -** A stack is similar to an array, except you are only allowed to push/pop (add/remove) from the end of the stack.
A stack follows the first in, last out, or FILO theme.

Since Python already has O(1) push (append) and pop (pop) operations, we do not need to use any libraries.

**Visual Examples**  
Visual of a stack being mutated, [click](https://cdn.programiz.com/sites/tutorial2program/files/stack.png){:target="_blank"} to view  

# Solution Statistics For Optimal Solution

**Time Spent Optimizing**  
10 minutes

**Time Complexity**  
O(n) - We must iterate through each element in the tokens list, resulting in the O(n) time complexity.
Since we do not perform any operations larger than O(1), the time complexity does not increase.

**Space Complexity**  
O(1) - There are never more elements in the num_stack than in the tokens list. 
num_stack is just an intermediary which increases and decreases throughout the execution of the for loop, resulting in the O(1) space complexity.

**Runtime Beats**  
93.75% of other submissions  

**Memory Beats**  
92.13% of other sumbissions  

# Optimized Solution  

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        num_stack = []

        # Iterate through each token
        for tok in tokens:
            match tok:
                # If the token matches any of the following, perform the 
                # corresponding operation
                case "*":
                    num_stack.append(num_stack.pop() * num_stack.pop())
                case "+":
                    num_stack.append(num_stack.pop() + num_stack.pop())

                # The order of the elements matters, so we must place each
                # element in an intermediary and then perform the operation
                case "-":
                    r, l  = num_stack.pop(), num_stack.pop()
                    num_stack.append(l - r)
                case "/":
                    r, l  = num_stack.pop(), num_stack.pop()
                    num_stack.append(int(l/r))

                # If it does not match any of the following, it is an integer, 
                # append it to the stack after converting it to an integer
                case _:
                    num_stack.append(int(tok))
                

        return num_stack[0]
```

# Solution Statistics For Original Solution

**Time Spent Coding**  
23 minutes

**Time Complexity**  
O(n<sup>2</sup>) - We must iterate through each element in the tokens list and perform one O(n) operation in the for loop, which increases our time complexity to O(n<sup>2</sup>).

**Space Complexity**  
O(1) - There are never more elements in the num_stack than in the tokens list. 
num_stack is just an intermediary that increases and decreases throughout the execution of the for loop, resulting in the O(1) space complexity. 
Although the same space complexity, the function creates a lot more intermediary values which causes the awful space complexity.

**Runtime Beats**  
11.74% of other submissions  

**Memory Beats**  
10.33% of other sumbissions  

# Original Solution  

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        def eval(join):
            opL, op, opR = join

            match op:
                case "*":
                    return opL * opR
                case "-":
                    return opL - opR
                case "/":
                    return int(opL/opR)
                case "+":
                    return opL + opR
            
        num_stack = []
        

        for tok in tokens:                      # O(n)
            if tok not in {"+","-","*","/"}:
                num_stack.append(int(tok))
            else:
                join = [tok]
                join.append(num_stack.pop())
                join.insert(0,num_stack.pop())  # O(n)

                num_stack.append(eval(join))
                

        return int(num_stack[0])
```

