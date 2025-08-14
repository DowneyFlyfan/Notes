---
id: Flow-Based Model
aliases: []
tags:
  - AI
sr-due: "2025-06-13"
sr-ease: 220
sr-interval: 1
---
# 问题描述

## 变量声明

- $x$是噪声, $x_1$是数据, 归一化时间$t \in [0,1]$ 

- $p_t(x)$是噪声分布, $q_t(x_1)$是数据分布

- $\phi_t(x)$是从$p$到$q$的**Unconditional Flow**

- $v_t(x; \theta)$是整个**理论分布**的Unconditional Flow的速度向量场

- $\psi_t(x)$是从$p_0(x | x_1)$到$p_1(x | x_1)$(即$q(x)$的逼近)的**Conditional Flow**

-  $u_t(x|x_1)$是整个**理论分布**的Conditional Flow的速度向量场

- $u_t(x)$是$p$到$q$的目标向量场，即学习目标  

## 背景介绍

- 原来的流是一步步转换得到的(离散的), 这篇文章加了一个时间变量$t$, 变成连续流了

# 定理

## Continuity Equation 及其Log形式

- [[../Calculus & Linear Algebra/Continuity Equations.md]]

## 无条件向量场得到条件概率路径
    
- **条件概率路径** $p_t(x)$**可以由无条件向量场**$u_t(x)$**得到**

$$
\begin{equation}
\begin{aligned}
\frac{d}{dt}p_t(x) &= \int \left(\frac{d}{dt}p_t(x|x_1)\right)q(x_1)dx_1 \\
&= -\int \text{div}\left(u_t(x|x_1)p_t(x|x_1)\right)q(x_1)dx_1 \\
&= -\text{div}\left(\int u_t(x|x_1)p_t(x|x_1)q(x_1)dx_1\right) \\
&= -\text{div}\left(u_t(x)p_t(x)\right) \\
\therefore u_t(x) &= \frac{\int u_t(x|x_1)p_t(x|x_1)q(x_1)dx_1}{p_t(x)} 
\end{aligned}
\end{equation}
$$

## 条件损失函数和无条件损失函数等效

### 描述

- $\mathcal L_{FM} || v_t(x; \theta) -u_t(x) ||$**和**$\mathcal L_{CFM} || v_t(x; \theta) - u_t(x | x_1) ||$的梯度相等

- 要点: $L_2$ 和**向量点乘**都可以求距离

### 证明

- $u_t(x)$是和$\theta$无关的量

$$
\begin{equation}
\begin{aligned}
\|v_t(x) - u_t(x)\|^2 &= \|v_t(x)\|^2 - 2\langle v_t(x), u_t(x)\rangle + \|u_t(x)\|^2 \\
\|v_t(x) - u_t(x|x_1)\|^2 &= \|v_t(x)\|^2 - 2\langle v_t(x), u_t(x|x_1)\rangle + \|u_t(x|x_1)\|^2
\end{aligned}
\end{equation}
$$

- 2种边缘概率积分下的第一项相等

$$
\begin{equation}
\begin{aligned}
\mathbb{E}_{p_t(x)}\|v_t(x)\|^2 &= \int \|v_t(x)\|^2 p_t(x)dx \\
&= \iint \|v_t(x)\|^2 p_t(x|x_1)q(x_1)dx_1dx \\
&= \mathbb{E}_{q(x_1), p_t(x|x_1)}\|v_t(x)\|^2
\end{aligned}
\end{equation}
$$

- 2种边缘概率积分下的第二项相等

$$
\begin{equation}
\begin{aligned}

\mathbb{E}_{p_t(x)}\left\langle v_t(x), u_t(x)\right\rangle &= \int \left\langle v_t(x), \frac{\int u_t(x|x_1)p_t(x|x_1)q(x_1)dx_1}{p_t(x)} \right\rangle p_t(x)dx \\
&= \int \left\langle v_t(x), \int u_t(x|x_1)p_t(x|x_1)q(x_1)dx_1 \right\rangle dx \\
&= \int \left\langle v_t(x), u_t(x|x_1)\right\rangle p_t(x|x_1)q(x_1)dx_1 dx \\
&= \mathbb{E}_{q(x_1),p_t(x|x_1)} \left\langle v_t(x), u_t(x|x_1)\right\rangle
\end{aligned}
\end{equation}
$$

- 因此，$L_{FM}$ 和 $L_{CFM}$ 关于$\theta$的梯度相等

## 从条件流到条件向量场

### 描述

- 条件流$\psi_t(x)$可以得到条件向量场$u_t(x | x_1)$

### 证明

$$
\begin{equation}
\begin{aligned}
\frac{d}{dt}\psi_t(x) &= u_t(\psi_t(x) | x_1) \\
\psi_t'(\psi_t^{-1}(y)) &= u_t(y) \quad \\
\psi_t^{-1}(y) &= \frac{y - \mu_t(x_1)}{\sigma_t(x_1)} \\
\psi_t'(x) &= \sigma_t'(x_1)x + \mu_t'(x_1) \\
u_t( \psi_t(x) | x_1) &= \frac{\sigma_t'(x_1)}{\sigma_t(x_1)}(y - \mu_t(x_1)) + \mu_t'(x_1) \\
u_t(x | x_1) &= \frac{\sigma_t'(x_1)}{\sigma_t(x_1)}(x - \mu_t(x_1)) + \mu_t'(x_1)
\end{aligned}
\end{equation}
$$

# 两种实现方式

- Diffusion Path

- Optimal Tract

# Insights
