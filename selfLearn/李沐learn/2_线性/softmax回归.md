# softmax回归

这是分类问题
---

表示分类数据的简单方法：独热编码（one-hot encoding）。 

        独热编码是一个向量，它的分量和类别一样多。 类别对应的分量设置为1，其他所有分量设置为0。

## 网络结构

![softmax回归是一种单层神经网络](./img/softmax回归是一种单层神经网络.png)

softmax回归也是一个单层神经网络

 由于计算每个输出O<sub>1</sub>
、O<sub>2</sub>
和O<sub>3</sub>
取决于 所有输入x<sub>1</sub>
、x<sub>2</sub>
、x<sub>3</sub>
和x<sub>4</sub>
， 所以softmax回归的输出层也是全连接层

        全连接层的参数开销


        在深度学习中，全连接层无处不在
        对于任何具有d个输入和q个输出的全连接层， 参数开销为O(dq)

## softmax运算

