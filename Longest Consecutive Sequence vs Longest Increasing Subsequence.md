Longest Consecutive Sequence → 要求数值连续，顺序无所谓。

```
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num_set = set(nums)
        max_len = 0

        for num in num_set:
            if num - 1 not in num_set:
                curr = num
                count = 1
                while curr + 1 in num_set:
                    curr += 1
                    count += 1
                max_len = max(max_len, count)

        return max_len
```

Longest Increasing Subsequence → 要求严格递增，顺序必须和原数组一致，数值可不连续。

```
from bisect import bisect_left
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        dp = []
        dp.append(nums[0])

        LIS = 1
        for i in range(1, len(nums)):
            if dp[-1] < nums[i]:
                dp.append(nums[i])
                LIS += 1
                continue

            idx = bisect_left(dp, nums[i])
            dp[idx] = nums[i]

        return LIS
```
