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

## Why LTI


