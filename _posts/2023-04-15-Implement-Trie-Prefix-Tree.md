---
title: Implement Trie (Prefix Tree)
date: 2023-04-15 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash table, string]
---

# Links  

Go to the [solution](#optimal-solution)  
Go to the [question](https://leetcode.com/problems/implement-trie-prefix-tree/){:target="_blank"} on LeetCode  

# My Thoughts  

**What Went Well**  
I had a great space complexity and solved the question quickly.

**What I Learned**  
I learned the bisect library and its use cases.

**How I Can Improve**  
I must keep learning and adding more libraries/algorithms to my repertoire.

**Comments**  
I hoped the simple solution would be the answer, but it was not.
Though I am impressed with how compact the optimal solution is and how intuitive it is after learning the bisect algorithm

# Algorithm/Data Structure Description

**Bisect -** The process of dividing something into equal parts. 
In this problem, we divide the array containing all the input strings and then search that array partition for an element most similar to the prefix. 
If the element we are looking for is in the array, we will return true, because the closest element should be a longer version of the prefix.

**Set (hash table) -** An unordered collection of distinct elements. Each element may only appear once.

**Hash Map/Dictionary -** A data structure that stores a collection of keys, each to their respective values. 
Each key may only appear once. 

# Solution Statistics For My Solution

**Time Spent Coding**  
8 minutes

**Time Complexity**  
O(n) - Each word in the dictionary must be iterated through, resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - Each inserted element is stored once, resulting in the O(n) space complexity.

**Runtime Beats**  
5.72% of other submissions  

**Memory Beats**  
96.12% of other sumbissions  

# Solution  

```python
class Trie:

    def __init__(self):
        self.dic = {}

    def insert(self, word: str) -> None:
        self.dic[word] = True

    def search(self, word: str) -> bool:
        return word in self.dic

    def startsWith(self, prefix: str) -> bool:
        if word in self.dic: return True

        for word in self.dic.keys():
            if word.startswith(prefix):
                return True

        return False

    ''' Set implementation
class Trie:

    def __init__(self):
        self.set = set()

    def insert(self, word: str) -> None:
        self.set.add(word)

    def search(self, word: str) -> bool:
        return word in self.set

    def startsWith(self, prefix: str) -> bool:
        if prefix in self.set: return True

        for word in self.set:
            if word.startswith(prefix):
                return True

        return False
    '''
```

# Solution Statistics For Optimal Solution

**Time Complexity**  
O(n) - Since each time we insert an element, we ensure the array remains sorted, we reduce the bisect search time to O(log n + m), where m is the length of the prefix. Unfortunately, this increases the insertion of an element to O(n), resulting in the O(n) time complexity.

**Space Complexity**  
O(n) - We store each value input value twice, so the space complexity really is n + n, but constant multiples of n are ignored, resulting in the O(n) space complexity.

**Runtime Beats**  
100% of other submissions  

**Memory Beats**  
94.9% of other sumbissions  

# Optimal Solution  

```python
# from bisect import bisect, insort
class Trie:

    def __init__(self):
        self.words = set()
        self.sorted_words = []
        
    def insert(self, word: str) -> None:
        self.words.add(word)
        insort(self.sorted_words, word)         # O(n)

    def search(self, word: str) -> bool:
        return word in self.words

    def startsWith(self, prefix: str) -> bool:
        index = bisect_left(self.sorted_words, prefix)      # O(log n + m)
        if index == len(self.sorted_words):
            return False
        return self.sorted_words[index].startswith(prefix)  # O(m)
```
