---
id: Loss_Functions
aliases: []
tags:
  - AI
---

#  CrossEntropyLoss  

- For **Index** and **Probabilities**

- -log(真实概率/总的概率)加权 

$$
\begin{equation}
\begin{aligned}
\ell(x, y) &= L = \{l_1, \ldots, l_N\}^\top \\ 
\quad l_n &= -w_{y_n} \log \frac{\exp(x_{n, y_n})}{\sum_{c=1}^C \exp(x_{n, c})} \cdot 1\{y_n \neq \text{ignore_index}\} \\ 
\ell(x, y) &= 
\begin{cases} 
\sum_{n=1}^N \frac{1}{\sum_{n=1}^N w_{y_n} \cdot 1\{y_n \neq \text{ignore_index}\}} l_n, & reduction = mean \\ 
\sum_{n=1}^N l_n, & reduction = sum \\ 
\end{cases} \\ 
\quad l_n &= -w_{y_n} \log \frac{\exp(x_{n, c})}{\sum_{i=1}^C \exp(x_{n, i})} \cdot y_{n,c} \\ 
\ell(x, y) &= 
\begin{cases} 
\sum_{n=1}^N \dfrac{1}{N} l_n, & reduction = mean \\ 
\sum_{n=1}^N l_n, & reduction = sum \\ 
\end{cases}
\end{aligned}
\end{equation}
$$


| Loss Function | Formula |
|---|---|
| MSE Loss (L2 Loss) | $\sum_i (y_{out,i} - y_{target,i})^2$ |
| L1 Loss | $\sum_i \|y_{out,i} - y_{target,i}\|$ |
| BCE Loss | $- [ y \cdot \log(y^{pred}) + (1 - y) \cdot \log(1-y^{pred}) ]$ |
| TVLoss (Total Variational Loss) | $$Loss = \int \left[ \left(\frac{du}{dx}\right)^2 + \left(\frac {du}{dy}\right)^2 \right]^{\dfrac{\beta}{2}} dx dy \\ &= \sum_{w,h} \left[(x_{w,h - 1} - x_{w,h})^2 + (x_{w + 1, h} - x_{w,h})^2 \right]^{\dfrac{\beta}{2}}$$ |
