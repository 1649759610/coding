# 岛屿数量2

给定一个m 行， n列的二维网格，该网格最开始全部被水充满，我们可以通过addLand 来将一个位置的水变为陆地。给定一组坐标来执行addLand操作，输出每次操作完后岛屿的数量。一个岛被水包围并且它是通过水平方向或垂直方向上相邻的陆地连接而成的。可以假设网格的4个边均被水包围。

备注：任何通过DFS和BFS来解决的图类问题都有一个前提：图示处理好的。而本题图是动态变化的，因此此时使用DFS或BFS来处理效率就不那么高了。因此，如果需要求动态变化的图的连通分量数量，使用并查集效率更高。

```python
class Solution:
    class UnionFind:
        def __ini__(self, grid):
            self.count  = 0
            n, m = len(grid), len(grid[0])
            self.parent = [0 for _ in range(m * n)]
            self.rank = [0 for _ in range(m * n)]
            for i in range(n):
                for j in range(m):
                    if grid[i][j] == "1":
                        self.parent[i*n+j] = i*n + j
                        self.count += 1

        def find(self, i):
            if self.parent[i] != i:
                self.parent[i] = self.find(self.parent[i])
            return self.parent[i]

        def union(self, i, j):
            root_i, root_j = self.find(i), self.find(j)
            if root_i == root_j:
                return
            
            if self.rank(root_i) > self.rank(root_j):
                self.parent[root_j] = root_j
            elif self.rank(root_i) < self.rank(root_j):
                self.parent[root_i] = root_j
            else:
                self.parent[root_j] = root_i
                self.rank[root_i] += 1
            
            self.count -= 1

        def getCount(self):
            return self.count
        
        def setCount(self, count):
            self.count = count
        
        def setParent(self, i, val):
            self.parent[i] = val

    def numIslands(self, n, m, positions):
        if n <= 0 or m <= 0:
            return []
        
        ans = []
        grid = [[0 for _ in range(m)]  for _ in range(n)]
        uf = UnionFind(grid)

        for position in positions:
            r, c = position
            uf.setCount(uf.getCount() + 1)
            uf.setParent(r*n + c, r*n + c)
            grid[r, c] = "1"

            if r -1 >= 0 and grid[r-1][c] == "1":
                uf.union(r*n+c, (r-1)*n+c)
            
            if r+1<n and grid[r+1][c] == "1":
                uf.union(r*n+c, (r+1)*n+c)

            if c - 1 >= 0 and grid[r][c-1] == "1":
                uf.union(r*n+c, r*n+(c-1)) 
            
            if c + 1 < m and grid[r][c+1] == "1":
                uf.union(r*n+c, r*n+(c+1))
            
            ans.append(uf.getCount())

        return ans

```
