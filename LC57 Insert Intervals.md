```
def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        res = []
        new_start, new_end = newInterval
        inserted = False

        for start, end in intervals:
            if end < new_start:  # 当前区间在 newInterval 左边
                res.append([start, end])
            elif start > new_end:  # 当前区间在 newInterval 右边
                if not inserted:
                    res.append([new_start, new_end])
                    inserted = True
                res.append([start, end])
            else:  # 有重叠
                new_start = min(new_start, start)
                new_end = max(new_end, end)

        if not inserted:
            res.append([new_start, new_end])

        return res
```
