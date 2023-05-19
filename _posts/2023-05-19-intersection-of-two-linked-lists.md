---
title: Intersection of Two Linked Lists
date: 2023-05-19 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, linked list, two pointer]
---


### View *Intersection of Two Linked Lists* on [LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n + m) - We must iterate through each list at least once, taking n as the length of listA and m as the length of listB; this causes our time complexity to be O(n + m).

**Space Complexity**  
O(1) - The number of variables created is independent of n or m, resulting in the O(1) space complexity.

**Runtime Beats**  
84.88% of other submissions  

**Memory Beats**  
100% of other sumbissions  

## Explanation
Before iteration, we must initialize our "pointers" `l1` and `l2` to listA and list, respectively.  

We will then begin iterating until each "pointer" represents the same node in the list, and this can only ever occur at the intersection due to how we are iterating.

With each iteration of the while loop, we will reassign our pointer to its next node if the current node is `None.` 
If it is `None,` we will set the pointer equal to the opposite list starting node. 

If there is an intersection, we will return the node that both pointers are equal to.  
If there is **no** intersection, eventually, the nodes will both be equal to `None`, and we will return that.

# Algorithms Used

**Two Pointer Algorithm -** An algorithm typically used to search a list where opposite ends of the list share a relationship that will be compared to determine some outcome.

For this problem, that condition would be if the elements are equal to the same node.

**Visual Examples**  
An array being transformed into a set, [click](https://drive.google.com/file/d/1LRyxh8Lfi00T58I4HRA6jOKPuO87s40F/view?usp=sharing){:target="_blank"} to view  

The two-pointer algorithm being performed on a list where the condition summing to 6, [click](https://usblog.teamblind.com/wp-content/uploads/2022/06/Two-Pointers-Coding-Interview-Problem.png){:target="_blank"} to view  


## Solution  

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        l1,l2=headA,headB
        while l1!=l2:
            l1=l1.next if l1 else headB
            l2=l2.next if l2 else headA
        return l1
```