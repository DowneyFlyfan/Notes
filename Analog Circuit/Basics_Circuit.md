---
id: Basics_Circuit
aliases: []
tags:
  - Circuit
---

# Resistance Calculation

> For Transistor, only SSM are linear and can be measured using **Testing Source Method**

> To calculate resistance looking into a transistor circuit:

- **GND all independent Sources**

> Resistance Looking into **Source** for any transistor is $\dfrac{1}{g_m + g_{mb}}$ (**Not Considering CLM**)

# Norton/Thevenin's Theorem

> Any linear two-terminal network can be represented by a Thévenin equivalent (**voltage source in series with a resistance**) or a Norton equivalent (**current source in parallel with a resistance**).

$$
\begin{equation}
\begin{aligned}
V &= V_{the} - I R_{the} \\
I &= I_{no} - \frac{V}{R_{no}} 
\end{aligned}
\end{equation}
$$

$V_{the}$ and $I_{no}$ can be measured by setting $I=0(oc)$ and $V=0(sc)$

# Temp

## Differential Pairs

### Large-Signal Model

- 

### Small-Signal Model

- SuperPosition & Half-Circuit

- $V_S$ doesn't change

- Differential Mode + CM

- CM makes no gain for Vx - Vy

- 
