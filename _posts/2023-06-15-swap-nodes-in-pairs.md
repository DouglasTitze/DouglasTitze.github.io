---
title: Swap Nodes in Pairs
date: 2023-06-15 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, linked list]
---

### View *Swap Nodes in Pairs* on [LeetCode](https://leetcode.com/problems/swap-nodes-in-pairs/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
20 minutes

**Time Complexity**  
O(n) - The algorithm must iterate through each node in the list at least once and perform O(1) operations at each node, resulting in the O(n) time complexity.

**Space Complexity**  
O(1) - The number of variables created is independent of the length of the input list, resulting in the O(1) space complexity.

**Runtime Beats**  
94.79% of other submissions  

**Memory Beats**  
92.32% of other sumbissions  

## Explanation 
Before performing logic, verify that the `head` node is not any and that `head.next` is not any; if the conditions are not met, then `return head.`

If the conditions are met, save the `adjacent` and `next_pair` nodes. `next_pair` is the `head` node of the next pair that will be used as an argument for the recursive call of the function. Assign `adjacent.next` to point at the head node and `head.next` to point at the recursive function call because the next node may change after another iteration of `swapPairs` and must not be statically assigned.

Once the recursive calls end, `head.next` will be appropriately assigned and connected with the other swapped pairs. Since the algorithm is complete, return the new head of the list `adjacent.` This is because `head` and `adjacent` swapped places, and if this line is omitted, the algorithm will not successfully connect each pair after termination and leave many dangling pointers.

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
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head or not head.next: return head

        adjacent = head.next
        next_pair = adjacent.next

        adjacent.next = head
        head.next = self.swapPairs(next_pair)

        return adjacent
```