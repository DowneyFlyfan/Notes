---
id: Differential_Amplifier
aliases: []
tags:
  - Circuit
---

# Basic Differential Pairs

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

> Two methods for analysis

- SuperPosition & Half-Circuit

- $V_S$ doesn't change

- Differential Mode + CM

- CM makes 0 gain for $V_X - V_Y$

> DP with Degeneration

- Trade Gain for Linearity

- Split $I_{SS}$ in 2 to fix the problem (induce more noise)

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

## Gilbert Cell
