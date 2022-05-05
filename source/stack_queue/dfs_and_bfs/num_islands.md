# 岛屿数量（第200题）

给定一个由1（陆地）和0（水）组成的二维网格，用其计算岛屿的数量。一个岛被水包围，并且它是通过水平方向或垂直方向相邻的陆地连接而成的。你可以假设网格的4个边均被水包围。

备注：按照上下左右4个方向进行dfs遍历，并将遍历到的网格点设置为『0』，即都设置为水。

```python
# 解法1：DFS递归实现
class Solution:
    def numIslands(self, grid):
        if not grid and not grid[0]:
            return 0
        
        ans = 0
        n, m = len(grid), len(grid[0])

        def dfs(r, c):
            grid[r][c] = "0"
            # 向上搜索
            if r-1 >= 0 and grid[r-1][c] == "1":
                dfs(r-1, c)
            # 向下搜索
            if r+1 <n and grid[r+1][c] == "1":
                dfs(r+1, c)
            # 向左搜索
            if c-1 >= 0 and grid[r][c-1] == "1":
                dfs(r, c-1)
            # 向右搜索
            if c+1 < m and grid[r][c+1] =="1":
                dfs(r, c+1)
        
        for i in range(n):
            for j in range(m):
                if grid[i][j] == "1":
                    ans += 1
                    dfs(i, j)

        return ans

```


```python
# 解法2：DFS 非递归实现
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid and not grid[0]:
            return 0

        n, m = len(grid), len(grid[0])
        ans = 0

        def dfs(r, c):
            grid[r][c] = "0"
            stack = [(r,c)]
            while stack:
                r, c = stack[-1]
                if r -1 >= 0 and grid[r-1][c] == "1":
                    stack.append((r-1, c))
                    grid[r-1][c] = "0"
                    continue
                if r + 1 < n and grid[r+1][c] == "1":
                    stack.append((r+1, c))
                    grid[r+1][c] = "0"
                    continue
                if c - 1 >= 0 and grid[r][c-1] =="1":
                    stack.append((r,c-1))
                    grid[r][c-1] = "0"
                    continue
                if c + 1 < m and grid[r][c+1] == "1":
                    stack.append((r, c+1))
                    grid[r][c+1] = "0"
                    continue
                stack.pop()
        
        for i in range(n):
            for j in range(m):
                if grid[i][j] == "1":
                    ans += 1
                    dfs(i, j)

        return ans



```

```python
# 解法3：BFS实现
from collections import deque

class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        if not grid and not grid[0]:
            return 0
        
        n, m = len(grid), len(grid[0])
        queue = deque()
        ans = 0 

        for i in range(n):
            for j in range(m):
                if grid[i][j] == "1":
                    ans  += 1
                    grid[i][j] = "0"
                    queue.append((i, j))

                    while queue:
                        r,c = queue.popleft()

                        if r - 1 >= 0 and grid[r-1][c] == "1":
                            grid[r-1][c] = "0"
                            queue.append((r-1, c))
                        if r + 1 < n and grid[r+1][c] == "1":
                            grid[r+1][c] = "0"
                            queue.append((r+1, c))
                        if c - 1 >= 0 and grid[r][c-1] == "1":
                            grid[r][c-1] = "0"
                            queue.append((r, c-1))
                        if c + 1 < m and grid[r][c+1] == "1":
                            grid[r][c+1] = "0"
                            queue.append((r, c+1))
        
        return ans


```
