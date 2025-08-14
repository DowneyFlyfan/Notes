---
id: Misc for AI & Python
aliases: []
tags:
  - AI
---

# Misc for AI & Python
1.  torch.nn算出来的Loss是一个Dictionary  
      
    
2.  Curriculum Learning: 不从数据集中随机采样，而是按照特定顺序采样以实现 模型的快速收敛和Generalization  
      
    
3.  Sentinel Tokens：在填空式任务中，用于标记需要填空处的token  
    Padding Tokens： 保证每个输入的长度相同 (打padding token)  
      
    
4.  yield: 在函数中使用 yield 关键字时，函数将是一个生成器函数。  
    生成器函数每次执行到yield 语句时会暂停，返回当前的值给调用者，并在下一次调用时从暂停的地方继续执行  
      
    
5.  pickle 将文件存储为字节流 (Byte Stream)；将对象从字节流文件中恢复  
    utils.misc.savepickle(order, order_name) # Save it as binary Stream  
    order = utils.misc.unpickle(order_name)  # Recover an object from a binary file  
      
    
6.  数据流是描述数据如何在系统中传递和处理的概念  
      
    
7.  地面勘测是获得卫星图像的 ground truth 的最好的方式，但是成本也最高。不过容易出现图像的对齐问题  
      
    
8.   Markov Chain: 当前状态仅取决于上一状态的一系列事件的概率  
      
    
9.  RNN 结合了历史数据和当前输入，从而捕捉时间序列中的相互依赖关系,  (h_t = \sigma \Big( W_{hh} h_{t-1} +W_{hx} x_t + b_t)$  
      
    
10.  退化算子: 下采样、模糊、失真等使得图像分辨率降低或变模糊等操作  
      
    
11.  上游任务是训练一个通用的模型，下游任务是用于具体实际任务  
      
    
12.  **Quadrature Mirror Filters (QMFs)** 是一种滤波器设计，用于将信号分解为互补的频带。比如说高通滤波器
    
    (h\[n] = \lbrace 0.5, 0.5 \rbrace$ 对应的就是低通滤波器  (g\[n] = \lbrace 0.5, -0.5\rbrace$  
      
    
13.  矩阵点积  
    逐元素相乘后，每一行求和, **e.g.** A\*B 和 A\*B 的 矩阵点积后得到 A\*1的向量  
      
    
14.  MCTL 中的 Herding 方法: Picking neaerst neighbors of the average sample per class  
      
    
15.  Pretext Task: 伪任务，不是目标，是用来辅助训练的，比如说预测下一个单词，预测周围像素  
      
    
16.  Curriculum Learning: 由难到易学习数据，加快收敛速度  
      
    
17.  (softplus = \log ( 1 +e^x)$  
      
    
18.  Fully Fused MLP: 专门为CUDA加速的MLP  
      
    
19.  numpy CPU计算默认64位, pytorch gpu 计算默认32位  
      
    
20.  DataParallel封装的模型，会把模型**复制**多份给每个GPU, 数据**分成**多块给多个GPU, **梯度默认全部由第一个GPU求解  
      
    **
21.  **ill-posed -> Nonlocal Sparsity Regularizer, nonlocal similarity  
      
    **
22.  元组是由逗号定义的,而不仅仅是括号  
      
    
23.  Grounding 数据:  
    ![](paste-e4f2d8c5f242798027c237c0b1c2e6a9e442e93f.png)  
      
    
24.  Pareto Frontier(多目标优化问题的最优解曲线): 任何一个点都不能在某个目标上改进而不在另一个目标上变得更差  
      
    
25.  Semantic Segmentation 和 object detection 的区别:  
    前者会**精确到Patch** (有的时候甚至是单像素), 后者会用方框把目标框起来，**精确到Object  
      
    **
26.  指令微调: 用详细描述的图片作为数据集进行post-train  
      
    
27.  残差神经网络的残差指的是**期望和输入之间的差异**(R(x) = F(x) - x$, 即网络学习的部分
