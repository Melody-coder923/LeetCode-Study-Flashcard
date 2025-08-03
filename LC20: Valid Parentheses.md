# LC20: Valid Parentheses

---

## Concept  
Check if a string containing only `(`, `)`, `{`, `}`, `[` and `]` is a valid parentheses string.  
Valid means every opening bracket has a corresponding closing bracket in the correct order.

---

## Key idea  
Use a stack to track opening brackets. When a closing bracket appears, check if it matches the last opening bracket on the stack.

---

## Problem Constraints  
- String contains only the six bracket characters.  
- Empty string is valid.  
- Must efficiently handle large strings.

---

## Core Approach (Stack)  
- Initialize an empty stack.  
- Traverse each character in the string:
  - If it’s an opening bracket, push onto the stack.  
  - If it’s a closing bracket, check if the stack is empty or if the top element doesn’t match the corresponding opening bracket. If so, return False. Otherwise, pop from stack.  
- After traversal, if the stack is empty, return True; else False.

---

## Key Logic

```
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        mapping = {')': '(', ']': '[', '}': '{'}
        
        for ch in s:
            if ch in mapping:
                top = stack.pop() if stack else '#'
                if mapping[ch] != top:
                    return False
            else:
                stack.append(ch)
        
        return not stack
```

## Edge Case Handling
- Empty string → return True  
- String starts with closing bracket → return False  
- Mismatched pairs → return False  
- Leftover opening brackets in stack after traversal → return False  

## Common Examples
- `"()"` → True  
- `"()[]{}"` → True  
- `"(]"` → False  
- `"([)]"` → False  
- `"{[]}"` → True  

## Time & Space Complexity
- Time: O(n) → n is length of the string  
- Space: O(n) → stack space in worst case  

## Why This Solution Is Preferred in Interviews
- Simple and intuitive stack approach  
- Easy to explain and demonstrate step-by-step  
- Efficient with single pass and constant operations per character  
- Handles all edge cases clearly  

## Tags
- Stack  
- String  
- Matching  
- Bracket Validation  
- Edge Case Handling
