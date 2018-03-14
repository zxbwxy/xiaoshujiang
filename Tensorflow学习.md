---
title: Tensorflow学习
tags: tensorflow,machine learn
grammar_cjkRuby: true
---
[toc]
2018年03月12日 
### 一、环境搭建 


#### Anaconda安装
Anaconda 是一个用于科学计算的 Python发行版，让我们可以方便的进行包管理与环境管理。
1. 下载安装

Anaconda 安装包可以到 https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/ 下载。

TUNA 还提供了 Anaconda 仓库的镜像，运行以下命令,即可添加 Anaconda Python 免费仓库。

> conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ 
> conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/ conda config
> --set show_channel_urls yes

2. 创建python3.5运行环境
  Anaconda3默认安装的是Python3.6，但是目前tensorflow只支持python3.5，但是目前的tensorflow只支持python3.5，这个时候要重新创建一个python3.5的环境，具体步骤：

1创建一个名为python3.5的环境，命名为python35

打开Anaconda Prompt,输入 conda create --name python35 python=3.5

2安装完成后，激活和取消激活命令

激活：activate python35

取消激活：deactivate

这个时候可以在Anaconda3路径下envs下看到刚才创建的python35，每当我们激活python3.5时，系统的运行环境就在这个文件下面。

#### 安装Tensorflow
安装好了上述的python3.5的环境之后，先激活python35，我们这里要装的是gpu版

输入：pip install tensorflow-gpu
若pip下载速度太慢，设置下pip镜像源[^1]

完成后，虽然安装完成了，但是需要GPU加速，还需要安装cuda和cuDnn（专门为deep learning 准备的加速库）

Win10+Anaconda3下tensorflow-gpu环境配置
#### 安装CUDA Toolkit 9.0
 1. [下载安装exe文件](https://developer.nvidia.com/cuda-toolkit-archive)
    默认安装即可，会自动在环境变量添加
 2. 验证CUDA是否安装成功 
 
![查看cuda信息][1]

 3. 验证用户环境变量
 CUDA_PATH已经加到环境变量中了，然后把bin和lib/x64加到环境变量中
![enter description here][2]

#### CuDnn库下载

1. [下载zip文件](https://developer.nvidia.com/rdp/cudnn-download)

  ![enter description here][3]
2. 解压文件到CUDA目录
  　解压cudnn-9.0-windows10-x64-v7.zip，将解压的三个文件夹拷贝至CUDA目录，进行覆盖即可。默认文件夹在：  `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0` 

#### 验证
在tensorflow环境里打开python

```python
import tensorflow as tf
hello = tf.constant("Hello!TensorFlow")
sess = tf.Session()
print(sess.run(hello))
```
![gpu加速程序][4]





### 二、基本概念

***HelloWorld***

``` python
import tensorflow as tf
import numpy as np

# 使用 NumPy 生成假数据(phony data), 总共 100 个点.
x_data = np.float32(np.random.rand(2, 100)) # 随机输入
y_data = np.dot([0.100, 0.200], x_data) + 0.300

# 构造一个线性模型
# 
b = tf.Variable(tf.zeros([1]))
W = tf.Variable(tf.random_uniform([1, 2], -1.0, 1.0))
y = tf.matmul(W, x_data) + b

# 最小化方差
loss = tf.reduce_mean(tf.square(y - y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

# 初始化变量
init = tf.initialize_all_variables()

# 启动图 (graph)
sess = tf.Session()
sess.run(init)

# 拟合平面
for step in xrange(0, 201):
    sess.run(train)
    if step % 20 == 0:
        print step, sess.run(W), sess.run(b)

# 得到最佳拟合结果 W: [[0.100  0.200]], b: [0.300]
```
基本概念

使用 TensorFlow, 你必须明白 TensorFlow:

- 使用图 (graph) 来表示计算任务.
- 在被称之为 会话 (Session) 的上下文 (context) 中执行图.
- 使用 tensor 表示数据.
- 通过 变量 (Variable) 维护状态.
- 使用 feed 和 fetch 可以为任意的操作(arbitrary operation) 赋值或者从其中获取数据.


[^1]: http://blog.csdn.net/ipaomi/article/details/78466321  
  
  
  
  参考文献：
  https://www.cnblogs.com/elroye/p/7864988.html
  http://blog.csdn.net/lcb_coconut/article/details/79228759


  [1]: ./images/1520867629585.jpg
  [2]: ./images/1520867763992.jpg
  [3]: https://i.loli.net/2018/03/13/5aa78d29cde7d.jpg
  [4]: https://i.loli.net/2018/03/13/5aa79d428b6e7.jpg