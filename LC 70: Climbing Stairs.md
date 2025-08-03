# Leetcode 70: Climbing Stairs

## Problem

You are climbing a staircase. Each time you can either climb 1 or 2 steps.  
Given `n`, return the number of distinct ways to reach the top.

---

## Idea

This is a classic **Dynamic Programming** problem.  
It is equivalent to computing the `n`-th number in a **Fibonacci-like** sequence.

- At step `i`, you can reach it either from step `i-1` (1 step) or `i-2` (2 steps).
- So the total ways to reach step `i` is:  
  `dp[i] = dp[i-1] + dp[i-2]`

---

## Method 1: DP with Array

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 1:
            return 1
        dp = [0] * (n + 1)
        dp[0] = dp[1] = 1
        for i in range(2, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n]
```

- Time: O(n)
- Space: O(n)


### Method 2: Rolling Variables (Space Optimized)

Since `dp[i]` only depends on the last two values, we can reduce space to **O(1)**.

```
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 1:
            return 1
        a, b = 1, 1
        for _ in range(2, n + 1):
            a, b = b, a + b
        return b
```
- Time: O(n)  
- Space: O(1)

---

### Edge Cases

- `n = 0` → 1 way (stay at bottom)  
- `n = 1` → 1 way  
- `n = 2` → 2 ways (1+1 or 2)

---

### Tags

- Dynamic Programming  
- Fibonacci  
- Rolling Variables  
- Space Optimization  
- Recurrence

