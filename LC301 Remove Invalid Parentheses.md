```
class Solution:
    def removeInvalidParentheses(self, s: str) -> List[str]:
        def valid(s):
            count=0
            for c in s:
                if c=="(":
                    count+=1
                elif c==")":
                    count-=1
                    if count<0:return False
            return count==0
        
        q=deque([s])
        visited=set([s])
        found=False
        res=[]

        while q:
            size = len(q)
            found = False  # 每层重新设置
            
            for _ in range(size):  # 处理完整的一层
                current = q.popleft()
                if valid(current):
                    res.append(current)
                    found = True
                else:
                    # 生成邻居
                    for c in range(len(current)):
                        if current[c] not in ("(", ")"):
                            continue
                        next = current[:c] + current[c+1:]
                        if next not in visited:
                            visited.add(next)
                            q.append(next)
            
            if found:  # 处理完整层后再判断是否结束
                break
        return res
```
