---
id: Differential_Amplifier
aliases: []
tags:
  - Circuit
---

# Basic Differential Pairs

![](./imgs/Differential_Amplifier/Differential_Pair.png)

## Large-Signal Model

$$
\begin{equation}
\begin{aligned}
V_{in1} - V_{in2} &= V_{GS1} - V_{GS2} \\
&= \sqrt{\frac{2I_{D1}}{k_{n1}} } - \sqrt{\frac{2I_{D2}}{k_{n2}} }\\
\frac{1}{2} k_n ( V_{in1} - V_{in2} )^2 &=  (I_{SS} - 2 \sqrt{I_{D1} I_{D2}}) \\
4I_{D1}I_{D2} &= I_{SS}^2 - (I_{D1} - I_{D2}) \\
I_{D1} - I_{D2} &= \frac{1}{2}\mu_{n}C_{ox}\frac{W}{L}(V_{in1} - V_{in2})\sqrt{\frac{4I_{SS}}{\mu_{n}C_{ox}\frac{W}{L}} - (V_{in1} - V_{in2})^2} \\
&= \sqrt{\mu_{n}C_{ox}\frac{W}{L}I_{SS}}(V_{in1} - V_{in2})\sqrt{1 - \frac{\mu_{n}C_{ox}(W/L)}{4I_{SS}}(V_{in1} - V_{in2})^2} \\
G_m &= \frac{\partial (I_{D1} - I_{D2})}{\partial (V_{in1} - V_{in2})} \\
&= \sqrt{\mu_{n}C_{ox}\frac{W}{L}I_{SS}}\sqrt{1 - \frac{\mu_{n}C_{ox}(W/L)}{4I_{SS}}(V_{in1} - V_{in2})^2}
\end{aligned}
\end{equation}
$$

## Small-Signal Model

### SuperPosition (Neglecting CLM and body effect)

> $V_{out} = V_X$, the circuit acts as a common-source stage with source degeneration $R_S = 1/g_{m2}$. 

> $V_{out} = V_Y$, it acts as a source follower driving $M_2$, which after Thévenin equivalence becomes a common-gate stage.

![](./imgs/Differential_Amplifier/Differential_Pair_VY=Vout.png)

$$
\begin{equation}
\begin{aligned}
V_X|_{by \ V_{in1}} &= \frac{-R_D}{g_{m1} + g_{m2}}  \\
V_Y|_{by \ V_{in1}} &= \frac{R_D}{g_{m1} + g_{m2}}  \\
( V_X-V_Y )_{by \ V_{in1}} &= \frac{-2R_D}{g_{m1} + g_{m2}} \\
( V_X-V_Y )_{by \ V_{in2}} &= \frac{2R_D}{g_{m1} + g_{m2}} \\
\therefore A_{dm} &= \frac{-R_D}{g_{m1} + g_{m2}} 
\end{aligned}
\end{equation}
$$

- Not a very high gain

### Half-Circuit

> Lemma: $V_P$ stays the same given any differential input

![](./imgs/Differential_Amplifier/Half-Circuit.png)

$$
\begin{equation}
\begin{aligned}
\frac{V_X}{V_{in1}} &= -g_m R_D \\
\frac{-V_Y}{V_{in1}} &= -g_m R_D \\
\therefore A_{dm} &= -g_m R_D
\end{aligned}
\end{equation}
$$

- $V_S$ doesn't change

- Differential Mode + CM

- CM makes 0 gain for $V_X - V_Y$

> DP with Degeneration

- Trade Gain for Linearity

- Split $I_{SS}$ in 2 to fix the problem (induce more noise)

## CM + DM

$$
\begin{equation}
\begin{aligned}
\frac{V_X-V_Y}{V_{in,cm}} 
\end{aligned}
\end{equation}
$$

# CM

## Gain

$$
\begin{equation}
\begin{aligned}
A_{v,dm} &= -g_m R_D \\
A_{v,cm} &= \frac{R_D}{\dfrac{1}{g_m} + R_S} 
\end{aligned}
\end{equation}
$$

## Real Condition

> Real Current Source has a finite resistance $R_{SS}$

> Real Manufacturing makes $R_D$ different

- CM Variation has **significant impact** on Differential Output

> CM-DM Conversion induced by Mismatches between 2 transistors

$$
\begin{equation}
\begin{aligned}
A_{v, CM-DM} &= - \frac{\Delta g_m R_D}{(g_{m1} + g_{m2}) R_{SS} + 1} 
\end{aligned}
\end{equation}
$$

## CMRR

## MOS Load

- Current-Source Load (Low Gain)

- Diode-Connected Load (Low Voltage Swing)

- Parallel $R_D$ with Current-Source Load solves the above 2 problems

- Cascode Stage has very high gain

- [ ] ## Gilbert Cell
