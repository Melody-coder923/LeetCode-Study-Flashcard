```
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        grid= [[0]* n for _ in range(n)]
        left,right=0,n
        top,bottom=0,n
        count=0
        while left<right and top<bottom:
            for j in range(left,right):
                count += 1
                grid[top][j]=count
            top+=1
            for i in range(top,bottom):
                count += 1
                grid[i][right-1]=count
            right-=1
            if not (left < right and top < bottom):
                break
            for j in range(right-1,left-1,-1):
                count += 1
                grid[bottom-1][j]=count
            bottom-=1
            for i in range(bottom-1, top-1,-1):
                count += 1
                grid[i][left]=count
            left+=1
        return grid
```
