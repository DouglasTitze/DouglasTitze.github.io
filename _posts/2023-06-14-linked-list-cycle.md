---
title: Linked List Cycle
date: 2023-06-14 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list]
---

### View *Linked List Cycle* on [LeetCode](https://leetcode.com/problems/linked-list-cycle/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
2 minutes

**Time Complexity**  
O(n) - Although unknown, the entire list is iterated through until the cycle is found. If there is no cycle, the list is iterated through once, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of n, resulting in the O(1) space complexity.

## Explanation  
Before iterating through the list, create two pointers, both pointing to the head node.

Begin iterating `while` the fast pointer and its next node are not equal to None.
Increment the fast pointer by two nodes and the slow by one, then check if they are equal.

*   If true, then `return True`. This works since the node is checked and not the node's value, meaning they are only equal if they have the same `.next` elements and values.
*   If false, continue the while loop until broken, or the if statement is true.

If the `while` loop ever exists, there is a node that is None, which would be impossible to have in a linked list with a cycle; therefore, `return False`.

## Algorithm and Data Structure Used

**Fast and Slow Pointer (Floyd’s Tortoise and Hare Algorithm) -** A traversal method that utilizes two pointers originating at the head of the list. The slow pointer increments one node at a time, and the fast pointer increments faster (2,3... nodes at a time).

**Linked List -** Similar to a list or an array, except the data allocated for the list is generated as each new node is added, meaning the memory for the entire list may not be in consecutive memory. A linked list can not be indexed and must be traversed using a pointer.

**Visual Example**  
GIF showing how the algorithm works, [click](https://cdn.emre.me/2019-10-23-tortoise-and-hare.gif){:target="_blank"} to view 


## Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = slow = head

        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow: return True 

        return False
```