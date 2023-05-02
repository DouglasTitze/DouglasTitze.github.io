---
title: Course Schedule
date: 2023-04-20 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, depth-first search, hash map, hash table]
---

# Links  

Go to the [solution](#solution)  
Go to the [question](https://leetcode.com/problems/course-schedule/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I understood how to approach the problem and apply depth-first search to the hash map. 

**What Went Wrong**  
There were edge cases that I was unable to solve, which kept me from being able to solve all the test cases.

**What I Learned**  
I learned that using extra memory to solve a problem is okay. I constantly attempt to solve each problem optimally, which sometimes leaves me unable to solve it.

**How I Can Improve**  
I need to realize that solving the problem with more memory is better than not solving the problem at all.

**Comments**  
Since there are so many ways to approach this problem, finding a solution most similar to my approach was challenging. Thankfully I found [this](https://www.youtube.com/watch?v=EgI5nU9etnU){:target="_blank"} youtube video. I am interested in the other ways to solve this problem, so I will revisit it in a few weeks and attempt it again using a different data structure.

# Algorithm/Data Structure Description

**Hash Map/Dictionary -** A data structure that stores a collection of keys, each to their respective values. 
Each key may only appear once. 

**Set (hash table) -** An unordered collection of distinct elements. Each element may only appear once.

**Depth-First Search -** An algorithm for traversing a tree/graph data structure. 
The algorithm begins at the root node and searches its children until it can not search any deeper. 
Once the deepest node is met, the algorithm works backward, computing each node. 

In this problem, we can take any course as the root and its prerequisites as its children. 
Each child may have other children, which the algorithm will also search. 
The computation performed on each node is the code after the current node's children are added to the search stack (once our depth-first search function is called on the children). 
These computations are: emptying the course's prerequisite list and removing the current node from the visited set.

**Visual Examples**  
Depth-first search being performed on a tree, [click](https://he-s3.s3.amazonaws.com/media/uploads/9fa1119.jpg){:target="_blank"} to view  

# Solution Statistics  

**Time Complexity**  
O(n * m) - We will take n as the number of courses and m as the largest number of prerequisites a given course has.
We must search through every course n and each of its perquisites m, resulting in the O(n * m) time complexity.

**Space Complexity**  
O(n + m) - Our dictionary will always contain n keys, and our visited set will, at worst, have m elements, resulting in the O(n + m) space complexity.

**Runtime Beats**  
80.88% of other submissions  

**Memory Beats**  
49.81% of other sumbissions  

# Solution  

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        # Fill the dictionary with each course as the key and an empty
        # list as their value. If not done this way, our algorithm will not work
        preDic = {i:[] for i in range(numCourses)}      # O(n)

        # Append the prereqs to their respective course
        for course, pre in prerequisites:               # O(n)
            preDic[course].append(pre)

        visited = set()

        # Create our depth-first search (dfs) function
        def possible(course):

            # If a course is in our visited set, then we are
            # actively performing dfs on it, meaning there is a
            # cycle. Therefore it is impossible to complete this course
            if course in visited: return False

            # If the course has no prerequisites, return true
            if preDic[course] == []: return True
                
            visited.add(course)

            # Perfrom dfs on each prerequisite of the current course
            for pre in preDic[course]:                  # O(m)

                # If any children return false, then it is impossible
                # to complete this course
                if not possible(pre): return False
            

            # If a course has been successfully searched, remove it from the set
            visited.remove(course)

            # Since we know this course is possible to complete and we have searched
            # every prerequisite we can denote it as possible by assigning the course
            # an empty list as its value
            preDic[course] = []

            return True

        # Since each course is labeled from 0 - numCourses-1
        # We can iterate through this range instead of the prereq list
        for course in range(numCourses):            # O(n)
            if not possible(course): return False

        return True

```
