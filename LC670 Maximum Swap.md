# LeetCode 670: Maximum Swap

## Problem  
Given a non-negative integer, you can swap two digits at most once to get the maximum possible number. Return the resulting number.

## Key Idea  
Track the rightmost maximum digit for each position.  
If a smaller digit appears before a larger digit on its right, swapping them increases the number.

## Algorithm  
- Convert the number to a list of digits.  
- Traverse from right to left, tracking the current maximum digit and its index.  
- If a digit is less than the maximum seen so far, record the swap positions.  
- After the loop, swap the leftmost valid pair (greedy choice).  
- Return the new number.  
- If no swap found, return the original number.

## Complexity  
- Time: O(n)  
- Space: O(n)

## Notes  
- Greedy: perform the first valid swap that gives the highest number.  
- This avoids unnecessary swaps and guarantees the best result.
