# LC9: Palindrome Number — Initial Filter Tags

## Concept
- A palindrome number reads the same forward and backward.
- Must be handled using **integer operations** (not string conversion) to optimize.

## Problem Constraints
- Negative numbers cannot be palindromes.
- Numbers ending in 0 (but not 0 itself) are not palindromes due to leading zero after reversal.

## Core Approach (Optimized Numeric Method)
- Reverse **half of the number** and compare it with the remaining half.
- Stop when the reversed half is greater than or equal to the remaining part.

### Key Logic
```
while x > reverted:
    reverted = reverted * 10 + x % 10
    x //= 10
return x == reverted or x == reverted // 10
```
## Edge Case Handling & Early Return
- `x < 0` → return False
- `x % 10 == 0 and x != 0` → return False

## Even vs Odd Length Handling
- Even length: `x == reverted`
- Odd length: `x == reverted // 10` (ignore middle digit)

## Common Examples
- `121` → Palindrome  
- `-121` → Not palindrome  
- `10` → Not palindrome  
- `0` → Palindrome

## Time & Space Complexity
- **Time**: O(log₁₀ n) → Only half of the digits are processed  
- **Space**: O(1) → Constant space used

## Why This Solution Is Preferred in Interviews
- No string conversion  
- Avoids integer overflow (unlike full reversal)  
- Optimized in both logic and resource usage  
- Demonstrates mastery of numeric problem-solving

## Tags
- Palindrome
- Reverse Integer
- Optimized Comparison
- Edge Case Handling
- Early Return Optimization
- Two Pointer (conceptually)
