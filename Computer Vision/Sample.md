---
id: Sample
aliases: []
tags:
  - CV
---

# 经典采样方法

1.  Bilinear (**按面积加权**插值), Tri-linear (**按体积加权**插值)  

$$
\begin{equation}
\begin{aligned}
\mathbf{P}(x, y) &= (1 - x)(1 - y) \cdot \mathbf{P}_{00} + 
x(1 - y) \cdot \mathbf{P}_{10} + 
(1 - x)y \cdot \mathbf{P}_{01} + 
xy \cdot \mathbf{P}_{11}
\end{aligned}
\end{equation}
$$

- 先在水平方向插值, 再在垂直方向插值, 等效于 按面积加权 插值   
    
2. Lanczosa **(a越大，通带越宽，越接近低通滤波器)**

$$
\begin{equation}
\begin{aligned}
Lanczos(x) &= \frac{\sin(\pi x) \sin(\dfrac{\pi x}{a})}{(\pi x)^2}
\end{aligned}
\end{equation}
$$

3. Bicubic  

$$
\begin{equation}
\begin{aligned}
W(x) &= 
\begin{cases} 
(a+2)|x|^3 - (a+3)|x|^2 + 1 & \text{for } |x| \le 1 \\ 
a|x|^3 - 5a|x|^2 + 8a|x| - 4a & \text{for } 1 < |x| \le 2 \\ 
0 & \text{otherwise} 
\end{cases}
\end{aligned}
\end{equation}
$$
