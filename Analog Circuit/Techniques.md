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

# Black Impedance Rules (BIR)

# ZVTC

# Mason's Gain Formula

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
