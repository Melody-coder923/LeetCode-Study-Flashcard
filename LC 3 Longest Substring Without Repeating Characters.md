```
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        visited = {}
        maxlength = 0
        start = 0 
        for i, char in enumerate(s):
            if char in visited and visited[char] >= start:
                start = visited[char] + 1  
            visited[char] = i 
            maxlength = max(maxlength, i - start + 1)

        return maxlength
```
