# LC9: Palindrome Number — Initial Filter Tags

## Concept
- Negative numbers cannot be palindrome due to leading ‘-’ sign mismatch.
- Numbers ending with zero but not zero itself cannot be palindrome because reversed number loses leading zeros.

## Why
- Early elimination reduces unnecessary computation.
- Simplifies subsequent palindrome checks.

## Common Examples
- Negative: -121 → Not palindrome
- Ends with zero: 10 → Not palindrome
- Zero itself: 0 → Palindrome

## Interview Key Phrases
- Quickly filter out impossible cases to improve efficiency.
- Negative numbers have a sign mismatch when reversed.
- Trailing zeros in non-zero numbers cause reversed number to differ.
- Early return for these cases simplifies logic.

## Tags
- Palindrome
- Reverse Integer: reverted = reverted * 10 + x % 10
- Optimized Comparison: x == reverted（even length）or x == reverted // 10 (odd length)
- Edge Case Handling/ Early Return Optimization :if x < 0: return False;  if x % 10 == 0 and x != 0: return False

