# LC13: Roman to Integer

## Concept
- Convert a Roman numeral string to its integer value.
- Roman numerals follow additive and subtractive rules.

## Problem Constraints
- Roman numerals use specific symbols: I, V, X, L, C, D, M.
- Subtractive notation applies when a smaller numeral precedes a larger one (e.g., IV = 4).

## Core Approach (Right-to-Left Traversal)
- Traverse the string from right to left.
- Use a mapping from Roman symbols to integers.
- Add or subtract values based on comparison with the previous numeral.

## Key Logic
```
total = 0
prev_value = 0
for char in reversed(s):
    value = roman_map[char]
    if value < prev_value:
        total -= value
    else:
        total += value
    prev_value = value
return total
```

## Edge Case Handling
- All valid Roman numerals conform to subtractive rules.
- Input string guaranteed valid as per problem statement.

## Common Examples
- "III" → 3
- "IV" → 4
- "IX" → 9
- "LVIII" → 58
- "MCMXCIV" → 1994

## Time & Space Complexity
- Time: O(n) → Single pass through the string
- Space: O(1) → Constant space for mapping and variables

## Why This Solution Is Preferred in Interviews
- Simple, clean one-pass solution
- Uses constant extra space
- Shows understanding of Roman numeral rules and mapping
- Efficient and easy to implement

## Tags
- Hash Map
- String Traversal
- Greedy
- Simulation
