---
title: Insert Interval
date: 2023-03-31 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, array]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/insert-interval/){:target="\_blank"} on LeetCode

# My Thoughts  

**What Went Well**  
I solved the problem, made my final code understandable, and devised an easier way to check each case.

**What Went Wrong**  
My first attempt at solving this problem took well over half the total time, contained too many if-then-else statements, and was spaghetti code.

**What I Learned**  
I learned that sometimes it's necessary to abandon your code and start from the beginning; if you want code you **_and others_** can understand.

**How I Can Improve**  
Practice, practice, practice. 
With more practice, I could've realized that my first implementation would not work and saved some time.

**Comments**  
I was surprised by the lack of understandable code when looking at other submissions. 
Every submission consisted of 300 if statements or a compact implementation using lambda functions but with no explanation.

I'm not saying my code is the most understandable or has the best time complexity, but it is much better than the other submission.

# Solution Statistics

**Time Spent Coding**  
40 minutes

**Time Complexity**  
O(n) - Each element in the array is visited once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only seven new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.

**Runtime Beats**  
66.16% of other submissions  

**Memory Beats**  
45.93% of other sumbissions  

# Solution  

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        # Assign insert_i to the largest possible insert index to avoid errors
        insert_i = length = len(intervals)
        i = 0
        
        # While the index is < the length
        while i < length:
            # Make values more readable
            x,y = intervals[i][0], intervals[i][1]
            n,o = newInterval[0], newInterval[1]
            
            # If x is larger than o, then there are no values past this index that we can merge with
            if x > o:
                insert_i = i
                break

            # If y is less than n, then this interval is less than our newInterval, and we cannot merge
            elif y < n:
                # Add 1 to i, so the insert occurs after this index
                insert_i = i + 1

                # This is the only case we need to increment i becuase the while loop will continue
                # without mutating the list or breaking out of the loop
                i += 1

            # All other cases    
            else:
                # Merge the states by getting the smallest and largest values
                newInterval[0], newInterval[1] = min(x,n),max(y,o)
                # Remove the current interval
                intervals.pop(i)
                # Decrement the list to accurately represent the length 
                length -= 1
                continue
    
        intervals.insert(insert_i,newInterval)

        return intervals
```
