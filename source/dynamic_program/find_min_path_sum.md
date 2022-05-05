# 在矩阵中找到路径的最小和

题目描述：

给定一个矩阵，从上到下去计算一个路径的最小和，对一行中的第j个元素，在下一行只能访问到它的相邻元素j-1，j 和 j+1，求到最后一行路径的最小和。

如矩阵:  
[[1,2,3,4],  
[2,3,4,5],  
[3,4,5,6],  
[4,5,6,7]]  

第一行元素2只能访问第2行的234，第2行的3只能访问第3行的345，第3行的3只能访问45.
最终最小路径为1234，最小和为10

```python

matrix = [
  [3, 2, 1, 6],
  [7, 1, 4, 3],
  [9, 5, 2, 6]
]

m, n = len(matrix), len(matrix[0])
forward = matrix[0][:]

for i in range(1, m):
    tmp_forward = forward[:]
    for j in range(0, n):
        if j == 0:
            forward[j] = min(matrix[i][j] + tmp_forward[j], matrix[i][j] + tmp_forward[j+1])
        elif j == n-1:
            forward[j] = min(matrix[i][j]+tmp_forward[j], matrix[i][j] + tmp_forward[j-1])
        else:
            forward[j] = min(matrix[i][j] + tmp_forward[j], matrix[i][j]+tmp_forward[j-1], matrix[i][j]+tmp_forward[j+1])
    print(forward)

print(forward)
print(min(forward))






```

