# Normalization
*   Max-Min Norm & MaxAbs Norm  
    (\begin{aligned} x_{max-min} &= \frac{x - x_{min}}{x_{max} - x_{min}} \in \[0,1] \\ x_{max-abs} &= \frac{x}{x_{max}} \in \[-1,1] \end{aligned}$  
      
    
*   Z-Score Norm - 零均值归一化  
    (x_n = \frac{x - \mu}{\sigma}, \mu_n = 0, \sigma_n =1$  
      
    
*   L2 & L1 Norm  
    (\begin{aligned} x_{l2} &= \frac{ x_j }{\sqrt{\sum_{i}^n ||x_i||^2}} \\ x_{l1} &= \frac{ x_j }{\sum_{i}^n |x_i|} \end{aligned}$  
      
    
*   Sigmoid & tahn & Softmax Norm  
    (tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$  
    (sigmoid(x) = \frac{1}{1 +e^{-x}} \in (0, 1]$, For Binary Classification Problems, Gating Machanism  
    (softmax(x) = \frac{e^x}{\sum_{i=1}^n e^{x_i}}$ , For Multi-Class Classification Problem, Attention  
      
    
*   Dynamic Tanh  
    (y = \gamma \tanh(\alpha x) + \beta$, 三个系数的形状都是((c,)$  
      
    
*   LayerNorm & BatchNorm & GroupNorm  
    

1.  公式   
    (\begin{equation} \begin{aligned} \mathcal{X}_N &= \frac{x - \mu }{ \sigma + \epsilon } \cdot \gamma + \beta \\ \widehat{x} _{t+1} &= (1-m) \widehat{x} _t + mx_{new}, \mathbf{BN} \end{aligned} \end{equation}$  
      
    其中, Statistics的 (\mu$和(\sigma$用第二个公式更新  
      
    
2.  思考  
    

*   RMSNorm  
    (\begin{equation} \begin{aligned}\mathcal{X}_{N} &= \frac{x}{\sqrt{\dfrac{1}{N}\sum_i^n x_i^2} + \epsilon} \end{aligned} \end{equation}$  
    RMSNorm 省去了中心偏移，计算效率更高
