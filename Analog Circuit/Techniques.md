---
id: Techniques
aliases: []
tags: []
---

# Thevenin & Norton Theorems

| Feature | Thevenin Theorem | Norton Theorem |
| :--- | :--- | :--- |
| **Equivalent** | Linear network $\equiv$ $V_{th}$ (series) $R_{th}$ | Linear network $\equiv$ $I_N$ (parallel) $R_N$ |
| **Source Value** | $V_{th} = V_{oc}$ (Open-circuit voltage at A-B) | $I_N = I_{sc}$ (Short-circuit current through A-B) |
| **Resistance** | $R_{th}$ at A-B (V $\to$ short, I $\to$ open) | $R_N$ at A-B (V $\to$ short, I $\to$ open) |
| **Dep. Sources** | $R_{th} = V_{oc} / I_{sc}$ or use a test source | $R_N = V_{oc} / I_{sc}$ or use a test source |
| **Relationship** | $V_{th} = I_N R_{th}$ | $I_N = V_{th} / R_{th}$ |

# Blackman's Impedance Rule

$$
\begin{equation}
\begin{aligned}

\end{aligned}
\end{equation}
$$

# ZVTC

# Mason's Gain Formula

> Feedback $F$ is defined that if it is a negative feedback, it must be $-F$

| Symbol | Description |
| :--- | :--- |
| $r$ | Input |
| $x_i$ | Node Voltage $i$ |
| $g_i$ | Coefficient for circuit equation |
| $\Delta_i$ | $\Delta$ when other feedback paths which connect to it are deleted |
| $G_i$ | Forward Gain of path $i$ |
| $\Delta$ | $1 - \sum L_a + \sum L_a L_b - \ldots$ |
| $L_a$ | Every **loop gain** |
| $L_a L_b$ | Every 2 **unconnected** loop gains |

$$
\begin{equation}
\begin{aligned}
x_j &= \sum_{i=1}^{n} g_i x_i + r \\
(I - G) X &= R \\
x_{out} &= \frac{\det(A_k)}{\det(I-T)}  \\
&= \frac{ \sum_{i=1}^{n} G_i \Delta_i }{\Delta }
\end{aligned}
\end{equation}
$$

# Block Diagram

# Asymptotic Gain Relations (AGR)

$$
\begin{equation}
\begin{aligned}
G(s) &= G_{\infty }(s) \frac{T(s)}{1 + T(s)} + G_0(s) \frac{1}{1 + T(s)}  \\
T(s) &= -\frac{\alpha x_c(s)}{x_x(s)} \\
G_0(s) &= \underset{\alpha  \xrightarrow{} 0}{lim} G(s) \\
G_{\infty}(s) &= \underset{\alpha  \xrightarrow{} \infty }{lim} G(s)
\end{aligned}
\end{equation}
$$

# Log Diagram

# Stability

$$
\begin{equation}
\begin{aligned}
A(s) &= \frac{a(s)}{ 1 + a(s) f(s)} = \frac{a(s)}{1 + T(s)} 
\end{aligned}
\end{equation}
$$

> To be stable

- Poles are all in LHP

- For Nyquist Plot, net number of encirclement across (-1,0) equals to number of RHP poles of $T(S)$

> Ringing: Defined as oscillation that dies overtime

- System that rings are called marginally unstable

- Number of zeros - Number of poles = Number of clockwise encirclement
