---
id: Quantization
aliases: []
tags:
  - AI
---

# Quantization-Aware Training

## Forward

> Signed Quantization

$$
\begin{equation}
\begin{aligned}
W_c &= \text{clamp} (\dfrac{W}{\alpha_w } , -1, 1) \\
W_q &= \frac{\text{Round} (|W_c| (2^{b-1} - 1))}{2^{b-1} - 1} \alpha _w \text{sign}(W_c)  \\ 
W_{int} &= \text{Round} (W_c (2^{b-1} - 1)) \text{sign} (W_c)
\end{aligned}
\end{equation}
$$

> Unsigned Quantization

$$
\begin{equation}
\begin{aligned}
x_c &= \text{clamp} (\dfrac{x}{\alpha_x } , 0, 1) \\
x_q &= \frac{\text{Round} (x_c (2^{b-1} - 1))}{2^{b-1} - 1} \alpha_c \\
x_{int} &= \text{Round} (x_c (2^{b-1} - 1))
\end{aligned}
\end{equation}
$$

> Results with unsigned input and signed weights

$$
\begin{equation}
\begin{aligned}
y_q &= \frac{\alpha_w \alpha_q}{(2^b - 1)(2^{b-1} -1)}  y_{int}
\end{aligned}
\end{equation}
$$

## Backward

> Variables that anticipate backprop

$$
\begin{equation}
\begin{aligned}
W_{qb} &= \frac{\text{Round} (|W_c| (2^{b-1} - 1))}{2^{b-1} - 1}  \text{sign}  (W_c) \\
W_b &= \frac{W}{\alpha_w} 
\end{aligned}
\end{equation}
$$

> Grad Computation

- Assume that **Straight Trace Estimator (STE)** has a grad of 1

$$
\begin{equation}
\begin{aligned}
\text{mask} &= (W_b >1) \\
\frac{\partial L}{\partial W_q}_{new} &= (1-\text{mask} ) \times \frac{\partial L}{\partial W_q} \\
\frac{\partial L}{\partial \alpha} &= \frac{\partial L}{\partial W_q}  \frac{\partial W_q}{\partial \alpha } \\
&= \frac{\partial L}{\partial W_q}  ( W_{qb} + \alpha \frac{\partial W_{qb}}{\partial \alpha } ) \\
&= \frac{\partial L}{\partial W_q}  \big[ \text{mask} \times  \text{sign}(W_b) + (1-\text{mask}) \times (W_{qb} - W_b)  \big] \\
\end{aligned}
\end{equation}
$$
