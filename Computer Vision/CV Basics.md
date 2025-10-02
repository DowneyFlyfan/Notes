---
id: CV_Basics
aliases: []
tags:
  - CV
---

# 表示方法

| 类别 | 概念 | 描述 | 备注/公式 |
|---|---|---|---|
| **彩色表示** | **HSV (Hue, Saturation, Value)** | 另一种彩色图像表示方法，更符合人类对颜色的感知。 | |
| | Hue (色相) | 颜色种类，通常以角度表示。 | 如红、蓝、绿 |
| | Saturation (饱和度) | 颜色纯度或鲜艳程度。 | |
| | Value (明度) | 颜色亮度或暗度。 | |
| **灰度表示** | **Grayscale (灰度图)** | 每个像素只含一个强度值，表示亮度，无颜色信息。 | |
| | Intensity (亮度) | 通常由彩色图像通过加权平均R, G, B通道转换而来。 | 公式：`0.299R + 0.587G + 0.114B` |

# 梯度计算

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
\mathbf{h} &= \mathcal{F}^{-1}\left\{\frac{\mathcal{F}\{\mathbf{X}\}^{*}\circ\mathcal{F}\{\mathbf{Y}\}}{\mathcal{F}\{\mathbf{X}\}^{*}\circ\mathcal{F}\{\mathbf{X}\}+\lambda+\mu(\mathcal{F}\{\mathbf{d}_h\}^{*}\circ\mathcal{F}\{\mathbf{d}_h\}+\mathcal{F}\{\mathbf{d}_v\}^{*}\circ\mathcal{F}\{\mathbf{d}_v\})}\right\}
\end{aligned}
\end{equation}
$$
