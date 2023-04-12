---
title: Clone Graph
date: 2023-04-13 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [breadth first search, graph]
---

# Links  

Go to my [solution](#solution)  
Go to the [question](https://leetcode.com/problems/clone-graph/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I knew the steps to take to solve the problem and how to implement it.

**What Went Wrong**  
I did not properly understand the input data and was consistently getting undefined behavior.

**What I Learned**  
I got more practice with deques and breadth-first search, helping me retain the algorithm much better.

**How I Can Improve**  
Practicing with more challenging questions will allow me to encounter more confusing data structures and problems that will push my mindset and skills to grow as I complete and dissect them.

**Comments**  
Although I am upset that I could not complete this problem looking at the solution and understanding it helps me realize that I could have solved this problem had I encountered a larger variety of data structures. 

When creating this post, I re-ran the solution to analyze its statistics and got a range from 99.90% to 8.20% with the EXACT same code, so take the solution statistics with a grain of salt.

# Algorithm Description

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
It creates a deque of elements yet to be visited and then iterates through each level (similar properties) until there are no more elements to iterate through. 
In this example, the similar property would be the root neighbor (the first neighbor to add the node to the list). 

The proper definition for breadth-first search when not being applied to this specific problem can be found [here](https://en.wikipedia.org/wiki/Breadth-first_search){:target="_blank"}.

# Solution Statistics  

**Time Complexity**  
O(n) - Each node is visited once and passed through a while loop. Since this while loop has an O(1) time complexity, it results in an O(n) time complexity.

**Space Complexity**  
O(n) - Each element is duplicated into a new graph, resulting in the O(n) space complexity.

**Runtime Beats**  
99.90% of other submissions  

**Memory Beats**  
62.14% of other sumbissions  

# Solution  

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""

class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        if not node: return node
        
        # Initialize the deque with the first node
        q = deque([node])

        # Initialize the duplicate graph with the first node by 
        # creating a new Node instance. 
        # Assign that instance to the node value as the key
        clones = {node.val: Node(node.val, [])}

        # Iterate through the deque until it is empty
        while q:      
            cur = q.popleft() 

            # Set cur_clone equal to the new Node instance
            cur_clone = clones[cur.val]            

            # Iterate through each neighbor of the original node
            for node in cur.neighbors:

                # If the node is not in clones, then append it to the deque
                # and add its clone to the clones dictionary using the same
                # method as we did before the while loop
                if node.val not in clones:
                    clones[node.val] = Node(node.val, [])
                    q.append(node)
                    
                # Append all the neighbors to the current clones list
                # Although the values are not fully computed yet when we return 
                # clones they will be populated with the correct information
                cur_clone.neighbors.append(clones[node.val])
                
        # Return the clones graph
        return clones[node.val]

```
