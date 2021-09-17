# TextCNN实现

```python
import paddle
import paddle.nn.functional as F


class TextCNN(paddle.nn.Layer):
    def __init__(self, embedding_size, class_num, kernel_sizes, kernel_num):
        super(TextCNN, self).__init__()
        self.class_num = class_num
        self.kernel_sizes = kernel_sizes
        self.kernel_num = kernel_num
        self.embedding_size = embedding_size

        self.convs = [paddle.nn.Conv2D(1, kernel_num, (kernel_size, embedding_size)) for kernel_size in self.kernel_sizes]
        self.fn = paddle.nn.Linear(self.kernel_num * len(kernel_sizes), class_num)


    def forward(self, inputs):
        # inputs: batch_size, seq_len, hidden_size
        # conv: batch_size, kernel_num, length
        convs = [F.relu(conv(inputs)).squeeze(3) for conv in self.convs]
        # single pool_out： batch_size, kernel_num
        pool_out = [F.max_pool1d(block, block.shape[2]).squeeze(2) for block in convs]
        pool_out = paddle.concat(pool_out, axis=1)

        logits = self.fn(pool_out)

        return logits


if __name__ == '__main__':
    # inputs: batch_size, in_channels, seq_len, embedding
    inputs = paddle.randn(shape=[5,1,10,128])
    # embedding_size:128, class_num:14, kernel_size:[2,3,4], kernel_num:2
    textcnn = TextCNN(128, 14, [2,3,4], 2)

    logits = textcnn(inputs)

    print(logits.shape)



```
