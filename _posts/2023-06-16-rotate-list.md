---
title: Rotate List
date: 2023-06-16 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, linked list]
---

### View *Rotate List* on [LeetCode](https://leetcode.com/problems/rotate-list/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n) - Although the algorithm iterates through each node at most twice, each iteration performs only O(1) operations, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the length of the list, resulting in the O(1) space complexity.

**Runtime Beats**  
85.73% of other submissions  

**Memory Beats**  
75.14% of other sumbissions  

## Explanation  
The algorithm works by shifting all k nodes to the front of the linked list in one sweep instead of incrementally.

The high-level overview of each step is as follows:

1.  Record the length of the linked list.
2.  Point the last node of the list to the head node. (This can be done by using the same pointer from step 1 since it is already at the last node)
3.  Convert `k` into the number of steps it will take to reach the new tail of the fully rotated list.
4.  Increment a pointer (`new_tail`) to the new tail of the fully rotated list using the calculated `k.`
5.  Save the `new_head` in a variable (this is the node after the `new_tail`)
6.  Eliminate the cycle in the list by making the `new_tail` point to `None.`
7.  Return the `new_head` of the `k` rotated linked list. (Step 2 takes care of properly connecting `new_head` to the rest of the rotated linked list)

## Data Structure Used

**Linked List -** Similar to a list or an array, except the data allocated for the list is generated as each new node is added, meaning the memory for the entire list may not be in consecutive memory. A linked list can not be indexed and must be traversed using a pointer.

## Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        # not head -> no list or k == 0 -> no swap 
        if not head or k == 0:
            return head

        # Compute the length of the list
        length = 1
        counter_pointer = head
        while counter_pointer.next:
            length += 1
            counter_pointer = counter_pointer.next

        # Make the last node of the list point to the head of the list
        counter_pointer.next = head 

        # Convert k to a number from 0 to k-1
        k = k % length
        # Convert k into the number of nodes needed to get to the new_tail
        k = length-k-1
        new_tail = head
        for _ in range(k):
            new_tail = new_tail.next
        
        # Place the new_head into a variable
        new_head = new_tail.next

        # Elminiate the connection between the new_tail and the new_head; to avoid a cycle
        new_tail.next = None

        return new_head
```