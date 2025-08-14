---
id: LTI-Systems
aliases: []
tags: []
---

# Properties

## System Properties

| 性质 | 定义 | 特性 |
|---|---|---|
| **有记忆 (Memory)** | 系统的当前输出取决于过去或未来的输入/输出。 | 具有存储元件（如电容、电感、延迟单元）的系统。 |
| **无记忆 (Memoryless)** | 系统的当前输出仅取决于当前的输入。 | 不具有存储元件的系统，如电阻器。 |
| **时不变 (Time-Invariant)** | 系统的输入-输出关系不随时间推移而改变。 | 若 $y(t) = T[x(t)]$，则 $y(t-t_0) = T[x(t-t_0)]$。 |
| **线性 (Linear)** | 满足叠加原理（齐次性和可加性）。 | 若 $T[a_1x_1(t) + a_2x_2(t)] = a_1T[x_1(t)] + a_2T[x_2(t)]$。 |
| **可逆 (Invertible)** | 不同的输入总是产生不同的输出，存在一个逆系统可以恢复原始输入。 | 如果 $y(t) = T[x(t)]$ 且 $x(t) = T_{inv}[y(t)]$。 |
| **因果 (Causal)** | 系统的当前输出仅取决于当前和过去的输入。 | 无法预测未来的输入，实际物理系统通常是因果的。 |
| **稳定 (Stable) (BIBO)** | 有界输入产生有界输出（Bounded-Input Bounded-Output）。 | 对于任意有界输入 $|x(t)| < M_x$，存在有界输出 $|y(t)| < M_y$。 |

## 常见的例子

1. Accumulator

- 这个系统是可逆的, 即使x[n]和y[n]都不是单调的

$$
\begin{equation}
\begin{aligned}
y[n] &= \sum_{k=- \infty}^{n} x[k] \\
y[n] &= y[n-1] + x[n] \\
w[n] &= y[n] - y[n-1]
\end{aligned}
\end{equation}
$$

## LTI System

### Why LTI

- 从采样出发, 对信号采样可以看成是系统响应 **移位到每一个时间点后与信号相乘后求和**

- 线性 保证 **系统响应能被缩放**且能被**线性组合**

- 时不变 保证 **响应能平移到任何一个时间点**

### Properties
| 性质 | 定义 |
|---|---|
| **交换律 (Commutative Law)** | $x(t) \otimes h(t) = h(t) \otimes x(t)$ 或 $x[n] \otimes h[n] = h[n] \otimes x[n]$ |
| **结合律 (Associative Law)** | $(x(t) \otimes h_1(t)) \otimes h_2(t) = x(t) \otimes (h_1(t) \otimes h_2(t))$ <br> 或 $(x[n] \otimes h_1[n]) \otimes h_2[n] = x[n] \otimes (h_1[n] \otimes h_2[n])$ |
| **分配律 (Distributive Law)** | $x(t) \otimes (h_1(t) + h_2(t)) = (x(t) \otimes h_1(t)) + (x(t) \otimes h_2(t))$ <br> 或 $x[n] \otimes (h_1[n] + h_2[n]) = (x[n] \otimes h_1[n]) + (x[n] \otimes h_2[n])$ |
| **无记忆LTI系统冲激响应** | 无记忆LTI系统的冲激响应 $h(t)$ 必须是单位冲激函数 $\delta(t)$ 的常数倍，即 $h(t) = C\delta(t)$。对于离散系统， $h[n] = C\delta[n]$。 |
| **导数法则 (Derivative Property)** | 若 $y(t) = x(t) \otimes h(t)$，则 $\frac{d}{dt}y(t) = \frac{d}{dt}x(t) \otimes h(t) = x(t) \otimes \frac{d}{dt}h(t)$。 |

### Causal LTI 系统 ...

### Singularity Functions



# Convolution

## Linear Convolution

- 若$x$和$h$都是定义在实域上是 **离散 / 连续** 函数

### DTC

$$
\begin{equation}
\begin{aligned}
x[n] \otimes h[n] &= \sum_{k=-\infty}^{\infty}  x[k] \cdot h[n-k] \\
x(t) \otimes  h(t) &= \int_{-\infty}^{\infty}  x(\tau) \cdot  h(t - \tau) d\tau
\end{aligned}
\end{equation}
$$

### CTC

## Overlap

1. Overlap Add

- 采用**linear convolution**, 把卷积对象拆成**不重叠的多段**，用卷积核分别去卷，相邻两段之间Overlap的部分加起来(**Add**)

2. Overlap Save

- 采用**Circulant Convolution**， 把卷积对象拆成**Overlap的多段**, 用卷积核分别去卷, 循环卷积的**错误部分直接抛弃**，然后拼起来 卷积技巧 卷积技巧
