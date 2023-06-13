---
title: Delete Node in a Linked List
date: 2023-06-13 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, linked list]
---

### View *Delete Node in a Linked List* on [LeetCode](https://leetcode.com/problems/delete-node-in-a-linked-list/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(1) - The number of steps executed in the algorithm is independent of the input node, resulting in the O(1) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the input node, resulting in the O(1) space complexity.

## Explanation  
To "delete" the node there are two steps:

1.   Replace the nodes value with the value of the node infront of it.
2.   Replace the nodes `.next` node with the node infront of its next node, hence the `.next.next`.  

Since the problem specifies that after replacement the node will not be a tail node there are no check to perform prior to executing line 2.

## Data Structure Used

**Linked List -** Similar to a list or an array, except the data allocated for the list is generated as each new node is added, meaning the memory for the entire list may not be in consecutive memory. A linked list can not be indexed and must be traversed using a pointer.

## Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteNode(self, node):
        node.val  = node.next.val
        node.next = node.next.next
```