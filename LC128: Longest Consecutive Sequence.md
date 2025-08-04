# LeetCode 128: Longest Consecutive Sequence

## Problem Recap
Given an unsorted integer array, find the length of the longest consecutive elements sequence. The algorithm must run in **O(n)** time.

## Why Not Just Sort?
Sorting is straightforward but takes **O(n log n)** time, which does not meet the time complexity requirement. This suggests using a data structure that supports faster lookups, like a hash set.

## Key Insight: Use a HashSet for O(1) Lookups
- Insert all numbers into a HashSet for constant-time existence checks.
- The challenge is to efficiently find consecutive sequences without redundant work.

## Avoiding Redundant Work by Finding Sequence Start Points
- Instead of expanding sequences from every number, only start from numbers that are the **beginning of a sequence**.
- A number is a sequence start if **num - 1** is not in the set.
- From each start, count upwards to find the full consecutive sequence length.

## Analogy
Counting longest consecutive sequence is like counting people in lines. To avoid counting the same line multiple times, start counting only from the first person in each line.

## Summary
1. O(n) requirement suggests using a hash-based data structure.
2. Use a HashSet for fast lookups.
3. Identify sequence starts to avoid repeated counting.
4. From each start, count consecutive numbers upwards.
5. Return the maximum sequence length found.
