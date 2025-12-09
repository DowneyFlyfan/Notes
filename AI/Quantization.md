---
id: Quantization
aliases: []
tags:
  - AI
---

# Formulas

$$
\begin{equation}
\begin{aligned}
W_c &= \text{clamp} (\dfrac{W}{\alpha_w } , -1, 1) \\
W_{qs} &= \frac{\text{Round} (W_c (2^b - 1))}{2^b - 1}  \\
W_q &= W_{qs} \alpha_w
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
x_c &= \text{clamp} (\dfrac{x}{\alpha_x } , 0, 1) \\
x_{qs} &= \frac{\text{Round} (x_c (2^{b-1} - 1))}{2^{b-1} - 1}  \\
x_q &= x_{qs} \alpha_x
\end{aligned}
\end{equation}
$$

- The final quantized $W_q$ is $\text{Round}(W_c (2^b-1))$
