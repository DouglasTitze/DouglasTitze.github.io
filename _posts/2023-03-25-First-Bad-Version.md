---
title: First Bad Version
date: 2023-03-25 00:00:00 -400
categories: [Coding Questions, Easy, Search Algorithms]
tags: [python, binary search, array]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/first-bad-version/description/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I quickly solved the question.
Thanks to Thursday's question, I identified the optimal solution while implementing my initial approach.

**What I Learned**  
I, once again, refreshed my memory about the binary search algorithm.

**How I Can Improve**  
The approach I took was the best one I could have. 
Although I knew my first implementation could have been more optimal and, most definitely, easier to understand. 
This approach enabled me to ease into the task and contemplate the optimal solution in the back of my mind while I worked on my initial answer.

**Comments**  
It is essential to be able to solve a problem over finding the most optimal solution. 
Always get something on the page and work your way to an answer, even if it is not the most efficient. 
If you cannot develop an optimal solution within a reasonable amount of time, proceed with a solution you confidently implement.

# Algorithm Description

**Binary Search Algorithm -** A search algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  
  
My implementation involves continuously halving the search interval until the left and right indices converge to the same index. 
This is because multiple bad solutions may make it impossible to guarantee that the middle index is the first bad solution. 
Hence, the algorithm must reduce the search interval to a single element to ensure a correct solution.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view  

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

# Solution Statistics For The Optimal Solution

**Time Spent Optimizing**  
10 minutes  

**Time Complexity**  
O(n log n) - Fixed-time complexity due to the question. 
The algorithm halves each iteration's search interval, resulting in the O(n log n) time complexity. 
(Fastest possible time complexity for all search algorithms)  

**Space Complexity**  
O(1) - Only three new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.  

**Runtime Beats**  
89.60% of other submissions  

**Memory Beats**  
48.14% of other sumbissions  

# Optimal Solution  

```python
# The isBadVersion API is already defined for you.
# def isBadVersion(version: int) -> bool:

class Solution:
    def firstBadVersion(self, n: int) -> int:
        # Left index
        l = 0               
        # Right index
        r = n - 1

        while r >= l:       
            # Middle index = sum both indices, divide by 2, and floor the result
            m = (l+r)//2

            if isBadVersion(m):
                # -1 to avoid checking the same value twice and infinite looping
                r = m - 1   
            
            else:
                # +1 to avoid checking the same value twice and infinite looping
                l = m + 1  

        # Since the loop exits after the right index is greater than or equal to 'l'
        # 'l' will always hold the first bad version
        return l
```

# Solution Statistics For The Original Solution

**Time Spent Coding**  
10 minutes   

**Time Complexity**  
O(n * a) - As n approaches infinity, the fact that we increment by 10,000 does not matter. 
Also, the time it takes to interact with the API (a) affects our time complexity and is a bottle neck for our program's run time because we can safely assume it takes more time than incrementing i. 
In the end, each increment of n requires a call to a, resulting in the O(n * a).

**Space Complexity**  
O(1) - Only one new variable is created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.  

**Runtime Beats**  
5.90% of other submissions  

**Memory Beats**  
48.14% of other sumbissions  

# Original Solution

```python
class Solution:
    def firstBadVersion(self, n: int) -> int:
        # Edge case
        if n == 1:
            return int(isBadVersion(1))

        # Iterate until n at steps of 10,000
        # Max n is 2^31, so without an increased step, the program would timeout
        for i in range(0,n,10000):
            # If isBadVersion(i) == True:
            if isBadVersion(i):         
                break

        # i is saved from the previous for loop
        # Iterate from the previous interval (i-10,000) till n.
        # First bad will be found within 10,001 increments of i
        # If we have a small n, subtracting 10000 may result in a negative number, so use the largest starting index max(0,i-10000)
        for i in range(max(0,i-10000),n):
            if isBadVersion(i):
                return i

        return n
```
