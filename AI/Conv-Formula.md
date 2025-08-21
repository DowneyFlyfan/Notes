---
id: Conv-Formula
aliases: []
tags:
  - AI
---

# 卷积后图像大小 公式，常用组合

1. 公式

$$
\begin{equation}
\begin{aligned}
W_{new} = \lfloor\frac{W - K + 2P}{S}\rfloor + 1
\end{aligned}
\end{equation}
$$
    
2.  常用组合  

| K | P | S | 卷积后图像大小 |
|---|---|---|---------------|
| 1 | 0 | 1 | $W$           |
| 3 | 1 | 1 | $W$           |
| 4 | 1 | 2 | $\dfrac{W}{2}$ |
| 8 | 2 | 4 | $\dfrac{W}{4}$ |
