```
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        left=0
        countt=Counter(t)
        have,need_count=0,len(countt)
        window=Counter()
        n=len(s)
        minlength=float('inf')
        min_l, min_r = None, None
        
        for right, ch in enumerate(s):
            window[ch] += 1
            if ch in countt and window[ch] == countt[ch]:
                have += 1
            while have == need_count:
                if right - left + 1 < minlength:
                    minlength = right - left + 1
                    min_l, min_r = left, right
                window[s[left]]-=1
                if s[left] in countt and window[s[left]] < countt[s[left]]:
                    have -= 1
                left+=1
        
        return s[min_l:min_r+1] if minlength!= float('inf')  else ""
```
