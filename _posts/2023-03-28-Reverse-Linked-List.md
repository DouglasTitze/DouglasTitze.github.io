---
title: Reverse Linked List
date: 2023-03-28 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list]
---

# Links

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/reverse-linked-list/){:target="\_blank"} on LeetCode

# My Thoughts  

**What Went Well**  
I knew how to traverse a linked list and use its methods. 
I read the constraints and all the test cases before coding. 

**What Went Wrong**  
It has been a while since I've reviewed linked lists, but I decided to start coding immediately. 
Unfortunately, the initial solution I came up with was unsuccessful, and I had to start from scratch despite having already invested 12 minutes into solving the problem.

**What I Learned**  
I refreshed my memory on linked list traversal but realized how difficult it is if you haven't seen it in a long time.

**How I Can Improve**  
I've realized the importance of writing things out on paper rather than trying to push out a solution with no direction.

**Comments**  
After solving the problem, the submission for this question from July last year was quite shocking.
Be prepared for the craziest solution you've ever seen, [previous solution](#previous-solution).

# Data Structure Description

**Linked List -**  [It is explained here much better than I could summarize.](https://en.wikipedia.org/wiki/Linked_list){:target="\_blank"}

**Visual Examples**  
A Linked List being reversed, [click](https://programmercave0.github.io/assets/reverselinkedlist.png){:target="\_blank"} to view 

# Solution Statistics  

**Time Spent Coding**  
18 minutes

**Time Complexity**  
O(n) - We must iterate through all the elements in the list, resulting in the O(n) time complexity.  

**Space Complexity**  
O(1) - Only three new variables are created. 
The number of variables declared does not depend on the number of items in the list, resulting in the O(1) space complexity.  

**Runtime Beats**  
77.47% of other submissions  

**Memory Beats**  
89.12% of other sumbissions  

# Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # If the LinkedList has 0 or 1 element, there is nothing to reverse
        if head == None or head.next == None:
            return head

        prev = head
        cur = head.next

        # To avoid an infinite loop, we must make the head point to None
        head.next = None

        while cur.next != None:
            next_cur = cur.next
            cur.next = prev
            prev = cur
            cur = next_cur

        # Include or else you will omit the last element
        cur.next = prev
        return cur
```

# Previous Solution

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        n = ListNode()
        begin = n
        save = head
        count = 0
        
        if head is None:
            return None
        else:
            while head != None:
                count += 1
                head = head.next
            
            for i in range(count - 1,-1,-1):
                head = save
                for j in range(i):
                    head = head.next
                n.val = head.val
                if i != 0:
                    n.next = ListNode()
                    n = n.next
                else:
                    n.next = None
                
            return begin
```
