# Leetcode 271: Encode and Decode Strings

## Concept  
Design a method to encode a list of strings into a single string and decode it back without ambiguity. The solution must work even when strings contain special characters like `#`.

## Key Idea  
Prefix each string with its length followed by a special delimiter (e.g., `"#"`), ensuring precise extraction during decoding.

```
class Solution:

    def encode(self, strs: List[str]) -> str:
        res=""
        for word in strs:
            res += str(len(word)) + "#" + word
        return res

    def decode(self, s: str) -> List[str]:
        res=[]
        i = 0
        while i < len(s):
            # 1. 找到下一个 #
            j = i
            while s[j] != "#":
                j += 1
            length = int(s[i:j])        # 2. 截取长度部分
            i = j + 1                   # 3. 移动到字符串起始位置
            res.append(s[i:i+length])  # 4. 提取字符串
            i += length                # 5. 跳到下一个编码单元
        return res
```

## Approach

### Encode:
1. **Initialization:** Start with an empty result string.
2. **For each string in the list:**
   - Get the length of the string.
   - Concatenate `length + '#' + string` to the result.
3. **Return the result string** after processing all strings.

### Decode:
1. **Initialization:** Start with an empty list and an index `i = 0`.
2. **While `i` is within the bounds of the encoded string:**
   - Locate the next `#` to determine the boundary of the length prefix.
   - Extract the length (`int(encoded[i:j])`).
   - Extract the string of that length starting at `j+1`.
   - Append the extracted string to the result list.
   - Move `i` to the end of the current segment and repeat.
3. **Return the result list**.

## Edge Case Handling
- Empty input list `[]` → Encodes to an empty string `""`, decodes back to `[]`.
- Empty strings within the list `["", "a"]` → Should be properly encoded and decoded as `0##1#a`.

## Common Examples

### Example 1:
**Input:** `["hello", "world"]`  
**Encoded:** `"5#hello5#world"`  
**Decoded:** `["hello", "world"]`

### Example 2:
**Input:** `["leet", "", "code"]`  
**Encoded:** `"4#leet0##4#code"`  
**Decoded:** `["leet", "", "code"]`

---

## Summary
This problem tests your ability to:
- Design a simple, unambiguous serialization format.
- Correctly parse strings using delimiters and substring slicing.
- Handle edge cases like empty strings or special characters.
