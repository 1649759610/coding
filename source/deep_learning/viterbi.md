# Viterbi实现

```python

import numpy as np

def viterbi(emis, trans):
    alpha = [[0,0,0]]
    beta = [[-1,-1,-1]]
    n_steps, n_labels=emis.shape[0], emis.shape[1]
    for step_i in range(1, n_steps+1):
        alpha_i = [0]*n_labels
        beta_i = [-1]*n_labels
        for label_i in range(0, n_labels):
            if step_i==1:
                tmp_score = emis[step_i - 1][label_i]
            else:
                tmp_score = alpha[step_i-1] + trans[:,label_i]+emis[step_i-1][label_i]
            alpha_i[label_i] = np.max(tmp_score)
            beta_i[label_i] = np.argmax(tmp_score)

        alpha.append(alpha_i)
        beta.append(beta_i)

    max_last_label = np.argmax(alpha[-1])
    path = [max_last_label]
    for beta_i in reversed(beta[2:]):
        if beta_i[0]!=-1:
            max_last_label = beta_i[max_last_label]
            path.append(max_last_label)

    while path:
        print(f"{path.pop()} ", end="")


if __name__ == '__main__':
    # assume that the num of label is 3, total step is 5,  so you can define the emis and trans as follows
    n_labels = 2
    n_steps = 3
    emis = np.random.randn(n_steps, n_labels)
    trans = np.random.randn(n_labels, n_labels)
    print("emis:", emis)
    print("trans:", trans)

    viterbi(emis, trans)



```
