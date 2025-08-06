---
id: Img_Basics
aliases: []
tags: []
---

# 表示方法

## Intensity

亮度 = 0.299 * R + 0.587 * G + 0.114 * B

# 梯度

- 也可用于边缘检测

| 滤波器名称 | 垂直方向核 (gv) | 水平方向核 (gh) |
|---|---|---|
| Naive2 | `[-1; 1]` | `[-1, 1]` |
| Naive3 | `[-1; 0; 1]` | `[-1, 0, 1]` |
| Roberts | `[-1, -1; 1, 1]` | `[-1, 1; -1, 1]` |
| Prewitt | `[-1, -1, -1; 0, 0, 0; 1, 1, 1]` | `[-1, 0, 1; -1, 0, 1; -1, 0, 1]` |
| Sobel | `[-1, -2, -1; 0, 0, 0; 1, 2, 1]` | `[-1, 0, 1; -2, 0, 2; -1, 0, 1]` |

# 去模糊

## 问题描述

$$
\begin{equation}
\begin{aligned}
y = x h + \epsilon
\end{aligned}
\end{equation}
$$

- 根据模糊图像$y$求解模糊核$h$, 这是一个**ill-posed problem**

## Data Fitting + Regularization

- **假设卷积核是中心对称的，这样卷积和正相关就是等效的**

- 否则用的时候需要把卷积核中心翻转一下

$$
\begin{equation}
\begin{aligned}
O(h) &= || y -Xh||^2 + \lambda ||h||^2 + \mu ( ||D_h h||^2 + ||D_v h||^2 \\
\frac{\partial O(h)}{\partial h}  &= -2yX + 2X^2 h + 2 \lambda h + 2\mu h(D_h^2 + D_v^2) = 0 \\
\mathbf{h} &= \frac{yX}{\lambda + X^2 + \mu(D_h^2 + D_v^2)}  \\
\mathbf{h} &= \mathcal{F}^{-1}\left\{\frac{\mathcal{F}\{\mathbf{p}\}^{*}\circ\mathcal{F}\{\mathbf{p}_e\}}{\mathcal{F}\{\mathbf{p}\}^{*}\circ\mathcal{F}\{\mathbf{p}\}+\lambda+\mu(\mathcal{F}\{\mathbf{d}_h\}^{*}\circ\mathcal{F}\{\mathbf{d}_h\}+\mathcal{F}\{\mathbf{d}_v\}^{*}\circ\mathcal{F}\{\mathbf{d}_v\})}\right\}
\end{aligned}
\end{equation}
$$
