---
title: Search in Rotated Sorted Array
date: 2023-05-02 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, binary search, array]
---

# Links  

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/search-in-rotated-sorted-array/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I created a solution, although not optimal, and discovered how to achieve O(log n) time complexity.

**What Went Wrong**  
I did not realize that performing a binary search on a sorted array resulted in O(log n) time complexity, and I believed implementing a binary search would be inefficient.

**How I Can Improve**  
I need to keep learning. As long as I keep posting, analyzing optimal solutions, and can at least get a functioning solution, then I am happy.

**Comments**  
The truly optimal solution has far worse statistics than my "Pythonic" solution. 
I hope this trend does not continue because it was very helpful in alerting me if I had a poor solution and should optimize it.

# Algorithm Description

**Binary Search Algorithm -** A sorting algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view 

# Optimal Solution Statistics  

**Time Complexity**  
O(log n) - The program performs a modified version of binary search O(n log n) on the input list, but the input list is already sorted, resulting in the O(log n) time complexity. 
With the modifications to the binary search algorithm, we can achieve the O(log n) time complexity due to the list having unique elements and being sorted.

**Space Complexity**  
O(1) - The number of variables created is independent from the number of elements in the input list, resulting in the O(1) space complexity.

# Optimal Solution  

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l = 0
        r = len(nums)-1

        while l <= r:
            mid = l+(r-l)//2
            if nums[mid] == target: return mid
            
            if nums[mid] >= nums[l]:
                if nums[l] <= target < nums[mid]:
                    r = mid -1
                else:
                    l = mid+1
            else:
                
                if nums[mid] < target <= nums[r]:
                    l = mid+1
                else:
                    r = mid-1                    
                     
        return -1
    
```

# Original Solution Statistics  

**Time Spent Coding**  
1 minute

**Time Complexity**  
O(n) - In the worst-case scenario, this solution would visit all the elements in the list, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - No new variables were created, resulting in the O(1) space complexity.

**Runtime Beats**  
98.72% of other submissions  

**Memory Beats**  
89.90% of other sumbissions  

# Solution  

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if target in nums:
            return nums.index(target)
        return -1
```