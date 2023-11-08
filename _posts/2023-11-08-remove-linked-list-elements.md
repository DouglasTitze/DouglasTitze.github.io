---
title: Remove Linked List Elements
date: 2023-11-08 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list]
---

### View *Remove Linked List Elements* on [LeetCode](https://leetcode.com/problems/remove-linked-list-elements/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
10 minutes

**Time Complexity**  
O(n) - Each element in the linked list must be visited, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - We are not allocating any more memory than what is passed in, resulting in the O(1) space complexity.

**Runtime Beats**  
92.15% of other submissions  

**Memory Beats**  
97.91% of other sumbissions  

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
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        # Change the list head until its value is not equal to the one being removed
        while head and head.val == val: head = head.next

        # Create a pointer to traverse the linked list without losing the head of it
        cur = head

        # Traverse the linked list until the header or its next element is null
        while cur and cur.next:

            # Remove next node from the list if it has a value equal to the one being removed
            if cur.next.val == val:
                cur.next = cur.next.next

            # Iterate to the next node if it has a valid value
            else:
                cur = cur.next

        return head
```