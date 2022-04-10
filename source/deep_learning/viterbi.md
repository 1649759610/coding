# Viterbi实现

```python

import numpy as np

def viterbi(emissions, transition):
    n_steps, n_labels = len(emissions), len(emissions[0])
    # 以标签i结尾的所有路径中的最大路径的分数
    alpha = np.zeros(shape=(n_steps, 2))
    # 在step 0， 用emissions[0]进行初始化
    alpha[0][0], alpha[0][1] = emissions[0][0], emissions[0][1]

    # 以标签i结尾的所有路径中的最大的那条路径，前一个时刻的标签
    beta = np.zeros(shape=(n_steps, 2), dtype=int)
    # 在step 0 ， 用[-1, -1]进行初始化
    beta[0][0], beta[0][1] = -1, -1

    for step_i in range(1, n_steps):
        for label_j in range(n_labels):
            tmp_score = alpha[step_i - 1] + transition[:, label_j] + emissions[step_i][label_j]
            # 记录信息
            alpha[step_i][label_j] = np.max(tmp_score)
            beta[step_i][label_j] = np.argmax(tmp_score)


    # 解码序列，首先找出最后一步中，哪个标签对应的序列是最大的
    max_label = np.argmax(alpha[-1])
    path = [max_label]
    for beta_i in reversed(beta):
        if beta_i[0] == -1:
            break
        max_label = beta_i[max_label]
        path.append(max_label)

    return list(reversed(path))


if __name__=="__main__":
    emissions = [[0.82, 0.28], [0.36, 0.76], [0.65, 0.57]]
    transition = [[0.1, 0.1], [0.1, 0.1]]
    emissions = np.array(emissions)
    transition = np.array(transition)

    path = viterbi(emissions, transition)
    print(path)


```
