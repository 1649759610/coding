# 并查集

并查集是一种树形结构，经常被用来处理一些不相交集合的查询和合并问题。具体而言，但我们需要快速连接任意两个节点，并且判断任意两个点是否连通的问题时，就可以使用并查集模板来实现。

**(1) 加权快速合并**  

首先使用parent数组来记录每个节点的父节点， 在初始情况下每个节点的父节点为本身（parent[i]=i）；并使用rank记录以每个节点为根的树的权值（树的高度）

然后借助这两个变量来实现以下两个操作：
- find(p): 当parent[p]!=p时，表示存在非本身的父节点，此时让p等于parent[p]，即向上寻找祖先节点，不断重复这个过程直到parent[p]==p，则p为祖先节点。

- union(p,q):通过find(p)和find(q)找到p和q的祖先节点，然后将权值小的祖先节点（以该节点为树的高度较矮）的父节点设置为另外一个权值大的祖先节点，即将较矮的树合并到较高的树中。

```python
class UnionFind:
    def __init__(self, n):
        # 每个节点的父节点
        self.parent = [i for i in range(n)]
        # 以该节点为根的树权值(树的高度)
        self.rank = [0 for i in range(n)]
        # 连通区域数量
        self.cnt = n
    
    def find(self, p):
        while p != self.parent(p):
            p = self.parent[p]
        return p
    
    def union(self, p, q):
        root_p, root_q = self.find(p), self.find(q)
        if root_p == root_q:
            return 
        if self.rank[root_p] > self.rank[root_q]:
            self.parent[root_q] = root_p
        elif self.rank[root_p] < self.rank[root_q]:
            self.parent[root_p] = root_q
        else:
            self.parent[root_q] = root_p
            self.rank[root_p] += 1
        self.cnt -= 1

```


**（2）路径压缩加权快速合并**

相较于加权快速合并，路径压缩加权快速合并的union(p,q)实现方式不变，只对find(p)进行优化。

优化方式：每当向上搜索到一个节点的祖先路径时，把搜索路径上的所有节点都指向祖先节点。下次再搜索这条路径上的节点的祖先节点时，将省去不断重复向上搜索的过程，有效加快find和union。


```python
def find(self, p):
    if p != self.parent[p]
        self.parentp] = self.find(self.parent[p])
    return self.parent[p]

```
