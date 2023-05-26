---
title: Merge Two Sorted Lists
date: 2023-05-26 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list]
---


### View *Merge Two Sorted Lists* on [LeetCode](https://leetcode.com/problems/merge-two-sorted-lists/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(n + m) - In the worst-case scenario, we must iterate through both lists, each having n and m elements, resulting in the O(n + m) time complexity.

**Space Complexity**  
O(n + m) - We are placing each element of each list into a new list, resulting in the O(n + m) space complexity.

## Explanation
Before iteration, we must initialize our linked list (`merge`), which we are returning, and our pointer (`p`) to traverse the linked list.

We will iterate through the lists until one has been fully traversed. This is because once traversed, `None` will be stored in the list variable, breaking the `while` loop conditional.

*   If the value at the `list1` is less than `list2`s, then we will add `list1`s node to the list and shift both `list1` and our pointer forward by assigning it to its own next element.

*   Similarly, if the previous if statement does not execute, we will follow the same steps except for `list2`s node.

Once our `while` loop exists, we add the lists which still contain elements to our merged list and then return the variable contacting our entire list `merge`.

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
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        merge = ListNode()
        p = merge

        while list1 and list2:
            if list1.val < list2.val:
                p.next = list1
                p = p.next
                list1 = list1.next
            else:
                p.next = list2
                p = p.next
                list2 = list2.next

        if list1: p.next = list1
        else:     p.next = list2

        return merge.next
```