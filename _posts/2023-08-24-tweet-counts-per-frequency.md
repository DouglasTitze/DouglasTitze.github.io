---
title: Tweet Counts Per Frequency
date: 2023-08-24 00:00:00 -400
categories: [Coding Questions, Medium]
tags: [python, hash map]
---

### View *Tweet Counts Per Frequency* on [LeetCode](https://leetcode.com/problems/tweet-counts-per-frequency/description/){:target="_blank"}  

## Statistics  

**Time Spent Coding**  
15 minutes

**Time Complexity**  
O(m) - The `getTweet...` method must iterate through all of `tweetName`'s tweets (m) to determine their groupings, resulting in the O(n) time complexity. All other methods are O(1).

**Space Complexity**  
O(n) - Every tweet must be added to the dictionary, resulting in the O(n) space complexity.

**Runtime Beats**  
69.74% of other submissions  

**Memory Beats**  
67.11% of other sumbissions  

## Explanation  
**_Code comments explain the program_**

## Data Structure Used 

**Hash Map (Dictionary) -** A data structure that maps keys to their values. Each key may only appear once.

## Solution  

```python
class TweetCounts:

    # Initialize a dictionary to track tweets
    def __init__(self):
        self.d = {}

    # Fill the dictionary with the tweetName as the key, and the time stamps of their tweets
    def recordTweet(self, tweetName: str, time: int) -> None:
        if tweetName in self.d:
            self.d[tweetName].append(time)
        else:
            self.d[tweetName] = [time]

    def getTweetCountsPerFrequency(self, freq: str, tweetName: str, startTime: int, endTime: int) -> List[int]:
        # Assign step, according to the input `freq`
        step = 1
        if freq.lower() == 'minute': step = 60
        elif freq.lower() == 'hour': step = 3600
        elif freq.lower() == 'day':  step = 86400

        # Assign the number of groups within the given range to nGroups
        nGroups = (endTime - startTime) // step + 1

        # Create a list with nGroups
        groups = [0] * nGroups

        # Iterate through all of the tweets from tweetName
        for n in self.d[tweetName]:

            # If the time stamp is outside of our search criteria, continue to the next value
            if n < startTime or n > endTime: continue

            # Calculate the group that n corresponds to and increment it
            group = (n - startTime)//step
            groups[group] += 1

        return groups
```