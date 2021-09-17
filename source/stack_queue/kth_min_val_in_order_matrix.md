# 有序矩阵中的第K小的元素

给你一个 n x n 矩阵 matrix ，其中每行和每列元素均按升序排序，找到矩阵中第 k 小的元素。
请注意，它是 排序后 的第 k 小元素，而不是第 k 个 不同 的元素。

```
输入：matrix = [[1,5,9],[10,11,13],[12,13,15]], k = 8
输出：13
解释：矩阵中的元素为 [1,5,9,10,11,12,13,13,15]，第 8 小元素是 13
```

## 解法
使用二分查找，最小值是左上角的元素，最大值是右下角的元素。  
如果当前有元素mid， 如果矩阵中大于等于mid的元素个数，大于等于k， 则说明要找的元素不大于mid，则right = mid。  
否则，如果小于k， 则left = mid + 1


```python 
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        min_val, max_val = matrix[0][0], matrix[-1][-1]
        n = len(matrix) 
        # 检查大于val的元素个数，是否大于等于k。
        def check(val):
            i,j = n-1,0
            nums = 0
            while i>=0 and j<n:
                if matrix[i][j] <= val:
                    nums += i+1
                    j += 1
                else:
                    i -= 1
            return nums >= k
        
        # 开始二分查找
        left, right = min_val, max_val
        while left < right:
            mid  = (left + right) // 2
            if check(mid):
                right = mid
            else:
                left = mid +1
        
        return left



```
