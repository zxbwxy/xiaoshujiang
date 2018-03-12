---
title: Tensorflow学习
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---
[toc]
2018年03月12日 
### 环境安装
http://blog.csdn.net/colourful_sky/article/details/78524382
http://blog.csdn.net/u010099080/article/details/53418159
http://blog.csdn.net/lcb_coconut/article/details/79228759
http://blog.csdn.net/ipaomi/article/details/78466321
http://blog.csdn.net/akon_wang_hkbu/article/details/78478513
一. 安装CUDA Toolkit 9.0
1. 下载 安装
https://developer.nvidia.com/cuda-toolkit-archive
2. 验证CUDA是否安装成功 
![enter description here][1]
 3. 用户环境变量配置
![enter description here][2]

二. 安装cuDNN 9.0
1. 下载
 https://developer.nvidia.com/rdp/cudnn-download
 2. cuDNN安装 
解压cudnn-9.0-windows10-x64-v7，将文件夹里如下图所示的三个文件夹分别拷贝至CUDA的安装目录的对应的文件夹即可。默认文件夹在： 
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0 
HelloWorld
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


  [1]: ./images/1520867629585.jpg
  [2]: ./images/1520867763992.jpg