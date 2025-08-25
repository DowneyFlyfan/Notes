---
id: Innovative-CNNs
aliases: []
tags: []
---

# Dynamic Convolution: Attention over Convolution Kernels  

![](./imgs/Dynamic_Conv.png)  

- 通过一个小的**attention**模块，针对不同的输入给卷积核加权  
      
# Deformable Convolution  

![](./imgs/Deformable_Conv.png)  

- 一个标准卷积的卷积核$k \in \mathcal R^{C_{out} \times C_{in} \times k \times k}$

- 一个**偏移量(方向向量) 卷积核$k \in \mathcal R^{2 \times C_{out} \times C_{in} \times k \times k}$ (x, y 两个方向上)
      
- 得到非整数值的卷积核坐标$p_k'= p+0 + p_n + \Delta p_n$, 通过**插值**获得整数坐标
      
- 但是**偏移量纯靠网络学习显然是不靠谱的**  

# Dynamic Filter Network  

![](./imgs/Dynamic-Filter-Network.png)

- 用 **condition A** $ 生成一个 (k \in \mathcal R^{d \times C_{out} \times C_{in} \times k \times k}, d = 1\ or \ HW$

- 在**全局或局部**上给B加一个条件  
    
# CANConv (Content Adaptive Convolution)  
    
![](./imgs/CANConv.png)

$$
\begin{equation}
\begin{aligned}
x(b,c,h,w) & \rightarrow unfold -> x(b,c\cdot k^2,h,w) -> kmeans \rightarrow x(b\cdot nc, ck^2, h,w) \rightarrow \\ 
\rightarrow permute &\rightarrow 1\times 1 \ Conv (c \cdot k^2 \rightarrow c_{hid} -> c) \rightarrow impermute \rightarrow x(b,c,h,w)
\end{aligned}
\end{equation}
$$

| Term | Description |
|---|---|
| permute | 按大小排序，每n个一组, 不够的打pad |
| impermute | permute的逆操作 |
| nc | number of clusters, 一个图分多少组 |
      
# ConvNeXt

- **V1**没有**GRN** 和 $\beta$

- V2适用于无监督学习，通过对通道加权，减少冗余通道影响，缓解了特征坍缩的问题

$$
\begin{equation}
\begin{aligned}
x(b,c,h,w) &\rightarrow 7\times 7 Group \ Conv(dim \rightarrow dim) \rightarrow LayerNorm \\ 
&\rightarrow 1 \times 1 Conv(dim \rightarrow 4\times dim) \rightarrow GeLu() \rightarrow GRN() \\ 
&\rightarrow 1 \times 1 Conv(4\times dim \rightarrow dim) \\ 
GRN(x) &= \gamma (\frac{xG_x}{\dfrac{1}{C}\sum_{i=1}^C G_x} ) + \beta + x \\ 
G_x &= \sqrt{\sum_{i=1}^{HW}||x_i||^2}
\end{aligned}
\end{equation}
$$
