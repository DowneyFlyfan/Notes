---
id: Power_Interconnect
aliases: []
tags:
  - Circuit
---

# Power & Interconnect

## Dynamic & Static Power

### Definition

> Caused by **charge/discharge** or even **short-circuit** (Dynamic), and **subthreshold leakage** (Static)

- Think of an inverter with a $C_L$ as load

- Energy charged/discharged to $C_L$ during a cycle are both

$$
\begin{equation}
\begin{aligned}
dE_C &=  QdV_C \\
E_C &= \int_{0}^{V_{DD}} C_L V_C dV_C \\
&= \frac{1}{2} C_L V_{DD}^2 \\
\therefore E_{total} &= C_L V_{DD}^2
\end{aligned}
\end{equation}
$$

### Activity factor

$$
\begin{equation}
\begin{aligned}
f_{sw} &= \alpha_{0 \xrightarrow{} 1}f_{clk} \\
P &= f_{sw} C_L V_{DD}^2 \\
&= \alpha_{0 \xrightarrow{} 1} f_{clk} C_L V_{DD}^2 \\
\end{aligned}
\end{equation}
$$

> Percentage of logic circuit is decreasing

## Interconnect

### Miller Coupling Effect

> Delay and Process: $nm \downarrow \xRightarrow{} \dfrac{\Delta T_d}{T_d} \uparrow$

### Elmore Delay

$$
\begin{equation}
\begin{aligned}
\tau &= \sum_{i}^{} R_{is} C_i
\end{aligned}
\end{equation}
$$

# Standard Cells


