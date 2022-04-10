# 前向算法实现

```python

import numpy as np

def forwardAlgorithm(emissions, transition):
    n_steps, n_labels = len(emissions), len(emissions[0])
    # 以标签i结尾的所有路径中的最大路径的分数
    alpha = np.zeros(shape=(n_steps, 2))
    # 在step 0， 用emissions[0]进行初始化
    alpha[0][0], alpha[0][1] = emissions[0][0], emissions[0][1]

    for step_i in range(1, n_steps):
        for label_j in range(n_labels):
            tmp_score = alpha[step_i - 1] + transition[:, label_j] + emissions[step_i][label_j]
            # 记录信息
            alpha[step_i][label_j] = np.sum(tmp_score)

    return alpha


if __name__=="__main__":
    emissions = [[0.82, 0.28], [0.36, 0.76], [0.65, 0.57]]
    transition = [[0.1, 0.1], [0.1, 0.1]]
    emissions = np.array(emissions)
    transition = np.array(transition)

    alpha = forwardAlgorithm(emissions, transition)
    print(alpha)

```
