---
title: Remove Nth Node From End of List
date: 2023-06-12 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, linked list, two pointer]
---

### View *Remove Nth Node From End of List* on [LeetCode](https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n) - At most, the list is iterated through once, resulting in the O(b) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the linked list, resulting in the O(1) space complexity.

**Runtime Beats**  
85.81% of other submissions  

**Memory Beats**  
75.36% of other sumbissions  

## Explanation
Before iterating through the linked list, create two pointers, `fast` and `slow`.

Iterate the `fast` pointer `n` nodes in front of the `slow` pointer.

Check if the `fast` pointer is `None`.
*   If this executes, then the pointer has exceeded the list, meaning the element to remove is the first element.

Begin iterating both pointers through the list until the `fast` pointer exceeds the list.

This means the `slow` pointer is now at the node before the node that needs to be removed. Execute `slow.next = ...` and then return the head of the list.

## Algorithm and Data Structure Used

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be identifying the nth element from the end of the list.

**Linked List -** Similar to a list or an array, except the data allocated for the list is generated as each new node is added, meaning the memory for the entire list may not be in consecutive memory. A linked list can not be indexed and must be traversed using a pointer.

**Visual Examples**  
The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view

## Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        fast = head
        slow = head
        for _ in range(n):
            fast = fast.next
            
        if fast == None:
            return head.next 

        while fast.next:
            slow = slow.next
            fast = fast.next

        slow.next = slow.next.next
        return head
```