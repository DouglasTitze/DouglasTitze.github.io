---
title: Palindrome Linked List
date: 2023-06-24 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list, two pointer]
---

### View *Palindrome Linked List* on [LeetCode](https://leetcode.com/problems/palindrome-linked-list/description/){:target="_blank"}  

## Statistics  

**Time Complexity**  
O(n) - Although `n/2` elements are traversed twice, this does not increase the overall growth rate from `n,` resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of `n,` resulting in the O(1) space complexity.

**Runtime Beats**  
98.48% of other submissions  

**Memory Beats**  
97.86% of other sumbissions  

## Explanation  

The program works in three parts:
1.   Find the middle of the linked list
2.   Reverse the first half of the linked list
3.   Iterate through the reversed half and the middle of the linked list till the end of the linked list is met

Steps 1 and 2 are implemented together; this is done to improve efficiency and simplify the program. The program only inverts the first half of the linked list since the slow pointer is iterating at one element and the fast pointer is iterating at two, so when the fast pointer meets the end of the linked list, the while loop exists.

The extra `if` statement ensures the slow pointer is on the correct element in case of uneven linked lists.

## Algorithm and Data Structure Used

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be identifying if the ith and n - ith elements are equal.

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
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        fast = slow = head
        prev = None

        while fast and fast.next:
            fast = fast.next.next
            next_node = slow.next
            slow.next = prev
            prev = slow
            slow = next_node

        if fast: slow = slow.next
        

        while prev and slow:
            if prev.val != slow.val: return False
            prev, slow = prev.next, slow.next

        return True
```