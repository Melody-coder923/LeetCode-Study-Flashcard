# LC12: Integer to Roman

## Concept
- Convert an integer to its Roman numeral representation.
- Use predefined Roman symbols and their values, including subtractive notation.

## Problem Constraints
- Input integer ranges typically from 1 to 3999.
- Must output a valid Roman numeral string following Roman numeral rules.

## Core Approach (Greedy Algorithm)
- Prepare a list of integer values and their corresponding Roman symbols, including subtractive cases.
- Iterate from largest to smallest value.
- While the current value can be subtracted from the number, subtract it and append the symbol to the result.

## Key Logic
```
values = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
symbols = ["M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"]

result = ""
for i in range(len(values)):
    while num >= values[i]:
        num -= values[i]
        result += symbols[i]
return result
```

## Edge Case Handling
- Input number within valid range (usually 1 to 3999).
- Correctly handle subtractive notations (4, 9, 40, 90, 400, 900).

## Common Examples
- 3 → "III"
- 4 → "IV"
- 9 → "IX"
- 58 → "LVIII"
- 1994 → "MCMXCIV"

## Time & Space Complexity
- Time: O(n) where n depends on the magnitude of the number (worst case, number of symbols added).
- Space: O(1) for symbol and value arrays, O(n) for output string.

## Why This Solution Is Preferred in Interviews
- Greedy approach aligns well with Roman numeral rules.
- Simple, intuitive, and easy to implement.
- Demonstrates understanding of problem constraints and encoding schemes.

## Tags
- Greedy
- Simulation
- Hash Map (mapping integer to symbol)
- String Manipulation
