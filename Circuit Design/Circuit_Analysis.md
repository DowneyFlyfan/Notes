---
id: Circuit_Analysis
aliases: []
tags:
  - Circuit
---

# Basic Concept

- SPICE (Simulation Program with Integrated Circuits Emphasize) Model

# Typical Instances

1. Analyze a traditional inverter

| Parameter | Description | Notes |
|---|---|---|
| $t_{pdr}$ | propagate delay rise time | from input 0.5V to output 0.5V|
| $t_{pdf}$ | propagate delay fall time | from output 0.5V to input 0.5V|
| $t_{pd}$ | propagate delay time |$t_{pd} = \dfrac{t_{pdr} + t_{pdf}}{2}$ |
| $t_{rt}$ | rising time | between 0.2V - 0.8V|
| $t_{ft}$ | falling time |between 0.8V - 0.2V  |

# Logical Efforts

## Linear Delay Model

$$
\begin{equation}
\begin{aligned}
d &= f (fan-out) + p(parasitic) \\
&= g(logical \ effort) h(electrical \ effort) + p
\end{aligned}
\end{equation}
$$

| Parameter | Description |
|---|---|
| $d$ | normalized delay of a gate |
| $g$ | $C_{in-gate} / C_{in-inverter}$, in which the gate and the inverter **delivers same current** |
|$h$|$C_{out}/C_{in}$. It is fan-out when **driver and loads are of same type**|
| $p$ | delay of the gate when it **drives zero load**, usually expressed in a constant times $p_{inv}$ |
| $p_{inv}$ | normalized parasitic delay for inverter, which is $3RC$ |

## Common LG, PG

![](./imgs/Circuit_Analysis/Logical_Effort.png)

![](./imgs/Circuit_Analysis/Parasitic_Effort.png)


## Path Delay

### Path Efforts

| Parameter | Description | Formula/Notes |
|---|---|---|
| $F$ | Path Efforts | $F = \sum_{i}^{} f_i = \sum_{i}^{} g_i h_i = GBH$ |
| $G$ | Path Logical Efforts | $G = \sum_{i}^{} g_i$ |
| $H$ | Path Electrical Efforts | $H = \frac{C_{out-path}}{C_{in-path}}$ (Uncommon: $\sum_{i}^{} h_i$) |
| $B$ | Path Branching Efforts | $B = \sum_{i}^{} b_i$ |

### Path Effort Delay

$$
\begin{equation}
\begin{aligned}
D_F &= \sum_{i}^{} d_i \\
&= D_F + P \\
&= \sum_{i}^{} f_i + P \\
f_i &= g_ih_i \\
P &= \sum_{i}^{} p_i
\end{aligned}
\end{equation}
$$

### Minimum Delay

- Delay is minimumed when **each stage bears same efforts**

$$
\begin{equation}
\begin{aligned}
f_i &= F^{1/N} \\
D &= NF^{1/N} + P \\
C_{in \ i} &= \frac{C_{out \ i} \times g_i }{\hat{f} } 
\end{aligned}
\end{equation}
$$
