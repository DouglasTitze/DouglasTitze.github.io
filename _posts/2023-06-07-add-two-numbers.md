---
title: Add Two Numbers
date: 2023-06-07 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, linked list, math]
---

### View *Add Two Numbers* on [LeetCode](https://leetcode.com/problems/add-two-numbers/){:target="_blank"}

## Statistics  

**Time Spent Coding**  
5 minutes

**Time Complexity**  
O(n) - Although each number and its sum are iterated through the resulting time complexity is O(n) since Big-O ignores constant multiples of n.

**Space Complexity**  
O(len(l1 +l2)) - The length of the sum of the numbers stored in l1 and l2 is the number of `ListNode`'s needed, resulting in the O(len(l1 +l2)) space complexity.

**Runtime Beats**  
56.69% of other submissions  

**Memory Beats**  
69.95% of other sumbissions  

## Explanation
Since each input is a linked list and not a number, the function `buildNum` is created to convert the input linked list to a number.

The function `buildNum` takes in a linked list and builds the entire number it contains. It does this by converting each digit from the linked list into a string and adding it to the front of the `res` string since the number is represented backward in the linked lists (e.g. 1 -> 2 = 21). Once the number is built, it is converted into an integer and returned.

Run this function for `l1` and `l2` and store their results in `n1` and `n2`. Add them, store the result in `tot`, and convert it into a string.

Initialize `head` as a `ListNode` and create a pointer to help incrementally add to the linked list.

Begin iterating backward (`[::-1]`) through each digit in the `tot` string and place its integer representation into a new `ListNode.` Then make the node at the pointer point to the new node, and move the pointer to this new node.

Once the `tot` string has been fully iterated, `return head.next` this is because the head node contains an empty ListNode, which would add a `0` to the front of the linked list.

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
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        def buildNum(linked_list):
            res = ''
            while linked_list != None:
                res = str(linked_list.val) + res
                linked_list = linked_list.next

            return int(res)

        n1 = buildNum(l1)
        n2 = buildNum(l2)

        tot = str(n1 + n2)
        
        head = ListNode()
        pointer = head
        
        for n in tot[::-1]:
            new = ListNode()
            new.val = int(n)
            pointer.next = new
            pointer = pointer.next

        return head.next
```