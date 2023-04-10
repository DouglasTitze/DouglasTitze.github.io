---
title: Middle of the Linked List
date: 2023-03-30 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list, two pointer]
---

# Links

Go to my [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/middle-of-the-linked-list/){:target="\_blank"} on LeetCode

# My Thoughts  

**What Went Well**  
I solved the problem quickly.

**What I Learned**  
I came across a new algorithm that I had heard mentioned before but have yet to delve into its details.

**How I Can Improve**  
I could have sought a more optimal solution before sifting through others' submissions. However, given the inconsistent statistics on LeetCode, my time and space complexity was acceptable.

**Comments**  
I am familiar with the two-pointer method but did not think of using it in such a way. 
This is an excellent algorithm to learn and is easy to remember.  

After implementing the optimal solution, I am getting worse solution statistics from LeetCode. 
Logically speaking, the optimal solution would be faster for larger lists, but the test data for this problem is not considerable enough to show the benefit of this algorithm.

# Algorithm Description

**Fast and Slow Pointer (Floyd’s Tortoise and Hare Algorithm) -** Begin with two points originating at the head of a list, and iterate the first by increments of one and the other by increments of two. 
If there is a loop in the list, the second pointer will catch up to the first. 
If there is no loop, we can identify the midpoint of the list once the second pointer reaches the end.

A more in-depth explanation can be found [here](https://www.geeksforgeeks.org/how-does-floyds-slow-and-fast-pointers-approach-work/){:target="_blank"}.

**Visual Examples**  
GIF showing how the algorithm works, [click](https://cdn.emre.me/2019-10-23-tortoise-and-hare.gif){:target="_blank"} to view 

# Solution Statistics For The Optimal Solution

**Time Complexity**  
O(n) - Each element in the array may be visited more than once, but no more than n elements are visited in total, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only two new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.

**Runtime Beats**  
23.43% of other submissions  

**Memory Beats**  
44.5% of other sumbissions  

# Optimal Solution

```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        slow = head
        fast = head

        # Handles the edge cases because of the conditionals
        # while fast != None and fast.next != None
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        return slow
```

# Solution Statistics For The Original Solution

**Time Spent Coding**  
7 minutes

**Time Complexity**  
O(n) - Each element in the array is visited, O(n), to get the length, and then the first half is visited again, O(n / 2), to reach the midpoint. We select the largest of the two, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - Only three new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.

**Runtime Beats**  
60.82% of other submissions  

**Memory Beats**  
44.28% of other sumbissions  

# Original Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # Handles edge cases
        if head == None or head.next == None:
            return head

        length = 0

        # Save a pointer to the head
        save_head = head

        # Iterate through the list to get the length
        while head != None:
            length += 1
            head = head.next

        half = int(length/2)

        # Iterate to the half point
        for i in range(half):
            save_head = save_head.next

        return save_head
```
