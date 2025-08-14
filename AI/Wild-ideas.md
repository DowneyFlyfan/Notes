---
id: Wild-ideas
aliases: []
tags:
  - AI
---

# No Prop (25.3)

1. 模型结构  
![](imgs/paste-2cb8c509668fc91c6424f94566ee3c2c3a0bf2da.png)  

- 左边是Discrete-Time, 右边是Continuous-Time  

2. 结构解释  

- 本质: Diffusion的翻版  

3. **Training**  
- 输入: 标签 $z_t$用和Diffusion一样的加噪方式处理, $z_0 \sim \mathcal N(0, I)$ , 时间 $t\rightarrow 编码 \rightarrow  MLP, 图像 \rightarrow 提取特征$  

- 输出: 图像类别预测(num_classes)  

4. **Inference的区别**  

- 输入: 标签$z_t$改成了上一层的输出  

5. Insights  
    暂时只能作用于分类任务，如果换成生成任务，标签怎么搞呢  
    可以用特征提取器来提取做标签, 但这样会大大增加训练时间，还不如不用NoProps  

# Hyper-Connection (24.9)

1. 结构  
![](imgs/paste-5d560769bdf325e0bb96c3027c7b2c305ef71c2d.jpg)  
    
2. Dynamic Update
![](imgs/paste-ef6f473f7ce5726ae33844f56ea7f986bec274f0.jpg)  
    
3. 流程 $h^0 \in R^{B \times N \times d}$, ($N$: Number of patches / Length of a sentence, $dC \times P^2 / Word \ Dim$
![](imgs/paste-c4068e7b238cdc090a5506f9a384ee4b1a8dc9ce.jpg)
