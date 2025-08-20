```
from collections import defaultdict, Counter

class Solution:
    def countTrapezoids(self, points: List[List[int]]) -> int:
        slope_to_intercepts = defaultdict(list)  # 斜率 -> [截距]
        midpoint_to_slopes = defaultdict(list)  # 中点 -> [斜率]

        for i, (x1, y1) in enumerate(points):
            for x0, y0 in points[:i]:
                dy = y1 - y0
                dx = x1 - x0
                slope = dy / dx if dx else inf
                intercept = (y1 * dx - x1 * dy) / dx if dx else x1
                slope_to_intercepts[slope].append(intercept)
                midpoint_to_slopes[(x1 + x0, y1 + y0)].append(slope)

        total = 0
        for intercepts in slope_to_intercepts.values():
            if len(intercepts) == 1:
                continue
            running_sum = 0
            for count in Counter(intercepts).values():
                total += running_sum * count
                running_sum += count

        for slopes in midpoint_to_slopes.values():
            if len(slopes) == 1:
                continue
            running_sum = 0
            for count in Counter(slopes).values():
                total -= running_sum * count  # 平行四边形会统计两次，减去多统计的一次
                running_sum += count

        return total

```
