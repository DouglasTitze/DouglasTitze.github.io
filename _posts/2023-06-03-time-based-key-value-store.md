---
title: Time Based Key-Value Store
date: 2023-06-03 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash map, binary search]
---

### View *Time Based Key-Value Store* on [LeetCode](https://leetcode.com/problems/time-based-key-value-store/){:target="_blank"}

## Statistics  

**Time Complexity**  
O(log n) - Initializing and setting a value takes O(1) time, but the get method takes O(log n) because we are performing a binary search on a sorted list.

**Space Complexity**  
O(n) - We must store all the input data given on a `set` method call, resulting in the O(n) space complexity.

**Runtime Beats**  
72.53% of other submissions  

**Memory Beats**  
59.42% of other sumbissions  

## Explanation
**TimeMap**
When the TimeMap class is initialized, we create the dictionary `dic`.

**Set**
When the set method is called, we check if the key has been stored before; if not, we must initialize the dictionary as an empty list.  
For all set calls, we will then append a tuple of both the value and its timestamp to the input key's list.

**Get**
When the get method is called, we create temporary variables: `values` to store all the values at the input key, `l` and `r` which are the binary search pointers, and `closest_val` that stores the closest value that is less than the input timestamp.

Begin the while loop until `l` is greater than `r.`  
We create and initialize the `mid` variable and extract the value and time at that index from the values list.

If the current time is less than the input timestamp, it may be the closest value to the input timestamp, so we increment the left pointer and re-assign the `closest_val.`  
If the time is greater than the timestamp, then we re-assign the right pointer and do not update `closest_val.`

Once the binary search `while` loop exits, the closest value to the input timestamp will be returned, and if no values are found, the default `closest_val` will be returned.

## Data Structure and Algorithm Used

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

**Binary Search -** A search algorithm that repeatedly halves the search interval until the target variable is found at the middle index.  

**Visual Examples**  
Illustration of key value pair mapping, [click](https://www.learnbyexample.org/wp-content/uploads/python/Dictionary-Key-Value-Pairs-Illustration.png){:target="_blank"} to view  

Binary search being performed on an array that contains the target, [click](https://ds1-iiith.vlabs.ac.in/exp/unsorted-arrays/binary-search/images/binary_search_stepwise.png){:target="_blank"} to view   

Binary search being performed on an array that does **not** contain the target, [click](https://storage.googleapis.com/algodailyrandomassets/tutorials-optimized/binarySearch1.png){:target="_blank"} to view

## Solution  

```python
class TimeMap:

    def __init__(self):
        self.dic = {}

    def set(self, key: str, value: str, timestamp: int) -> None:
        if key not in self.dic:
            self.dic[key] = []

        self.dic[key].append((value,timestamp))

    def get(self, key: str, timestamp: int) -> str:
        values = self.dic.get(key,[])
        l,r = 0, len(values)-1
        closest_val = ""

        while l <= r:
            mid = (l+r)//2
            val,time = values[mid]

            if time <= timestamp: 
                l = mid + 1
                closest_val = val
            else:
                r = mid - 1

        return closest_val
```