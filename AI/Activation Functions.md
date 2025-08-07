---
id: Activation Functions
aliases: 
tags:
  - AI
---


*   **各类激活函数及其适用范围**

1.  **ReLU：**适用于大多数标准深度学习任务，如图像分类和卷积神经网络，但在负值输入较多时可能会遇到问题。  
         
2.  **Leaky ReLU：**适合负值输入信息较重要或需要避免神经元死亡问题的网络，如生成模型或回归任务。  
      
    
3.  **PReLu:** 负数部分的(\alpha$可以学习  
      
    
4.  **ELU：**适用于对负值有处理需求且需要加速收敛的场景，如回归任务或更深的网络。  
      
    
5.  **Swish (SiLU)：**适用于非常深的网络，如在图像处理、目标检测或需要复杂非线性特征的任务。  
      
    
6.  **GeLU:** 平滑性高，处理连续输入和高度相关输入时发挥作用  
      
    
7.  **Softmax:** 用于多分类问题的输出  
      
    
8.  **Softplus**: ReLu的平滑版本  
      
    
9.  **Mish**: 长得跟Swish很想，计算开销也大些，实验证明效果也稍好一些  
      
    
10.  APTx: **Mish的简要计算版，但是没有实验验证  
    **![](paste-6452152d1f11a0da425c6dd8e92bfa6a8494547b.png)

*   公式  
    (\begin{gather} \begin{aligned} Leaky ReLu (x)&= \begin{cases} x & x > 0 \\\ \alpha x & x \le 0, \alpha \rightarrow 0 \end{cases} \\\ Swish(x)/SiLu(x) &= x \cdot \sigma(x) \\\ ELU(x) &= \begin{cases} x & x > 0 \\\ \alpha (e^x - 1) & x \le 0 \end{cases} \\\ erf(x) &= \frac{2}{\sqrt{\pi}} \int_{0}^x e^{-t^2} dt \\\ GeLu(x) &= \frac{1}{2} \lbrack 1 + erf( \frac{x}{\sqrt{2}}) \rbrack \\ Softmax(x)) &= \frac{e^x}{\sum_i e^{x_i}} \\\ Softplus(x) &= \ln (1 + e^x) \\ Mish(x) &= x \cdot \tanh ( \ln (1 + e^x)) \\ APTx(x) &= (\alpha + \tanh ( \beta x))\cdot \gamma x \end{aligned} \end{gather}$  
      
    
*   3种新激活函数的比较![](paste-f2eed32f156f625bd7c37db3daac9a154f7c580a.png)  
    显然, **H-SIREN能更快提取高频信息, 且不会过拟合或欠拟合**  
    因此**,** 在实践中，把SIREN的第一层激活函数改成H-SIREN效果会很好  
      
    
*   Siren的收敛
