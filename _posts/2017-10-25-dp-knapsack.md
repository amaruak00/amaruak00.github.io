---
layout: post
title: 동적 프로그래밍(Dynamic Programming) - 배낭문제(Knapsack) by python
tags: [Algorithm, Python]
author: amaruak00
excerpt_separator: <!--more-->
---

파이썬 3.5로 작성(knapSack.py)

```python
"""
# Returns the maximum value that can be put in a knapsack of
# capacity W

def knapSack(W, wt, val, n):

    # Base Case
    if n==0 or W==0:
        return 0

    # If weight of the nth item is more than Knapsack of capacity
    # W, then this item cannot be included in the optimal solution
    if(wt[n-1] > W):
        return knapSack(W, wt, val, n-1)

    # return the maximum of two cases:
    # (1) nth item included
    # (2) not included
    else:
        return max(val[n-1] + knapSack(W-wt[n-1], wt, val, n-1),
                   knapSack(W, wt, val, n-1))
"""

def knapSack(W, wt, val, n):
    K = [[0 for x in range(W+1)] for x in range(n+1)]

    #Build table K[][] in bottom up manner
    for i in range(n+1):
        for w in range(W+1):
            if i==0 or w==0:
                K[i][w] == 0
            elif wt[i-1] <= w:
                K[i][w] = max(val[i-1] + K[i-1][w-wt[i-1]], K[i-1][w])
            else:
                K[i][w] = K[i-1][w]

    return K[n][W]
           

# ----main

val = [10, 40, 30, 50]
wt = [5, 4, 6, 3]
W = 10
n = len(val)
print(knapSack(W, wt, val, n))
```

- Time Complexity : O(wn) when w = capacity of bag, n = number of items