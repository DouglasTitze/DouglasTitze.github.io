---
title: Find if Path Exists in Graph
date: 2023-07-26 00:00:00 -400
categories: [Coding Questions, Easy]
tags: [python, graph, breadth-first search]
---

### View *Find if Path Exists in Graph* on [LeetCode](https://leetcode.com/problems/find-if-path-exists-in-graph/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
7 minutes

**Time Complexity**  
O(n) - If the graph is fully connected all the nodes will be visited twice, but mutliples of the growth factor do not increase time complexity, resulting in the O(n) time complexity.

**Space Complexity**  
O(n * e) - Every node and all of their edges is stored in the graph, resulting in the O(n * e) space complexity.

**Runtime Beats**  
99.49% of other submissions  

## Explanation  
_The comments explain the majority of the code_

Using `n` an empty adjacency graph is built, and then using the `edges` list a that graph is then populated with each nodes connection.

## Algorithm Used  

**Breadth-first search -** A tree/matrix traversal algorithm that searches for elements with a given property. 
Create a queue of elements yet to be visited and then iterate through each level (similar properties) until there are no more elements of the same level. 


## Solution  

```python
class Solution:
    def validPath(self, n: int, edges: List[List[int]], source: int, destination: int) -> bool:
        # Build the bi-directional graph
        graph = {}
        for i in range(n):
            graph[i] = set()

        for a,b in edges:
            graph[a].add(b)
            graph[b].add(a)

        # Create varaibles to allow for breadth-first search
        visited = set()
        q = deque()
        q.append(source)

        # Continue searching until the queue is empty
        while q:
            # Iterate through all the nodes on the same level
            for _ in range(len(q)):
                s = q.popleft()
                
                # If the current node is the destination, return true
                if s == destination: return True
                
                # Otherwise, iterate through all the connected nodes and add them to the queue, if unseen
                for node in graph[s]:
                    if node not in visited:
                        visited.add(node)
                        q.append(node)

        return False
```