---
id: Normalization
aliases: []
tags:
  - AI
---

# Normalization

| Normalization Type            | Formula                                                                                                     | Description                                                                 |
| :---------------------------- | :---------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------- |
| Max-Min Norm                  | $\begin{aligned} x_{max-min} &= \frac{x - x_{min}}{x_{max} - x_{min}} \in [0,1] \end{aligned}$          |                                                                             |
| MaxAbs Norm                   | $\begin{aligned} x_{max-abs} &= \frac{x}{x_{max}} \in [-1,1] \end{aligned}$                               |                                                                             |
| Z-Score Norm                  | $x_n = \frac{x - \mu}{\sigma}, \mu_n = 0, \sigma_n =1$                                                     | 零均值归一化                                                                |
| L2 Norm                       | $\begin{aligned} x_{l2} &= \frac{ x_j }{\sqrt{\sum_{i}^n ||x_i||^2}} \end{aligned}$                         |                                                                             |
| L1 Norm                       | $\begin{aligned} x_{l1} &= \frac{ x_j }{\sum_{i}^n |x_i|} \end{aligned}$                                    |                                                                             |
| Sigmoid Norm                  | $sigmoid(x) = \frac{1}{1 +e^{-x}} \in (0, 1]$                                                              | For Binary Classification Problems, Gating Mechanism                        |
| Tanh Norm                     | $tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$                                                              |                                                                             |
| Softmax Norm                  | $softmax(x) = \frac{e^x}{\sum_{i=1}^n e^{x_i}}$                                                            | For Multi-Class Classification Problem, Attention                           |
| Dynamic Tanh                  | $y = \gamma \tanh(\alpha x) + \beta$                                                                      | 三个系数的形状都是((c,)                                                     |
| LayerNorm / BatchNorm / GroupNorm | $\begin{equation} \begin{aligned} \mathcal{X}_N &= \frac{x - \mu }{ \sigma + \epsilon } \cdot \gamma + \beta \\ \widehat{x} _{t+1} &= (1-m) \widehat{x} _t + mx_{new}, \mathbf{BN} \end{aligned} \end{equation}$ | Statistics的 $\mu$ 和 $\sigma$ 用第二个公式更新 (针对 BN) |
| RMSNorm                       | $\begin{equation} \begin{aligned}\mathcal{X}_{N} &= \frac{x}{\sqrt{\dfrac{1}{N}\sum_i^n x_i^2} + \epsilon} \end{aligned} \end{equation}$ | 省去了中心偏移，计算效率更高                                                |
      
    
# Insights

- RMSNorm 省去了中心偏移，计算效率更高
