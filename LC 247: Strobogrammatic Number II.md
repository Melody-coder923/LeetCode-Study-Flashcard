# Leetcode 247: Strobogrammatic Number II

## 🧩 Problem  
Given an integer `n`, return all the **strobogrammatic numbers** that are of length `n`.

A strobogrammatic number is a number that looks the same when rotated 180 degrees (e.g., "69", "88", "818").

---

## 💡 Idea  

This is a classic **recursive string construction** problem with **mirror symmetry**.

We generate the number **from outside to inside**, adding digit-pairs that are strobogrammatic on both ends.

```
class Solution:
    def findStrobogrammatic(self, n: int) -> List[str]:
        def build(m: int, total: int) -> List[str]:
            if m == 0:
                return [""]
            if m == 1:
                return ["0", "1", "8"]
            
            sub = build(m - 2, total)
            res = []
            for s in sub:
                for a, b in pairs:
                    # Avoid leading zeros at outermost layer
                    if m == total and a == "0":
                        continue
                    res.append(a + s + b)
            return res

        pairs = [("0", "0"), ("1", "1"), ("6", "9"), ("8", "8"), ("9", "6")]
        return build(n, n)
```

### Valid Strobogrammatic Pairs:
- `'0' <-> '0'`
- `'1' <-> '1'`
- `'6' <-> '9'`
- `'8' <-> '8'`
- `'9' <-> '6'`

### Base Cases:
- `n == 0` → `[""]`
- `n == 1` → `["0", "1", "8"]`

### Recursive Step:
- Recursively generate strobogrammatic numbers of length `n - 2`
- Add each valid pair to both ends of each shorter string
- For outermost layer: skip `"0"` pair to avoid leading zeros

---

## ⏱️ Complexity

- **Time:** `O(5^(n/2))`  
  Each level adds 5 options (digit-pairs), depth is `n // 2`.

- **Space:** `O(5^(n/2))`  
  For storing all possible results.

---

## ⚠️ Edge Cases

- `n = 0` → `[""]`  
- `n = 1` → `["0", "1", "8"]`  
- Leading zeros are **not allowed** for outermost digits when `n > 1`.

---

## 🏷️ Tags

- Recursion  
- Divide and Conquer  
- String Construction  
- Backtracking  
- Mirror Symmetry  
- Strobogrammatic Number  

