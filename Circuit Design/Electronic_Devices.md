---
id: Electronic_Devices
aliases: []
tags:
  - Circuit
---

# Transistors

## CMOS (Metal-Oxide-Semiconductor)

1. Diffusion Capacitance & Elmore Delay

- PUN / PDN (Pull-Up/Down Network) is modeled as RC Ladder to **greatly simplify** the circuit analysis

$$
\begin{equation}
\begin{aligned}
C_d &= \frac{dQ}{dV} \\
&\approx \tau \frac{dI}{dV} \\
&= \tau g_d
\end{aligned}
\end{equation}
$$

### Structure

![](./imgs/Devices/NMOS.png)

| Feature | Nitride Spacer | Shallow Trench Isolation (STI) | Poly Oxide |
|---|---|---|---|
| Main Function | Sidewall mask, defines LDD | Electrical isolation of devices | Interlayer dielectric (in floating-gate memory) |
| Main Material | Si$_{3}$N$_{4}$ | SiO$_{2}$ | SiO$_{2}$ |
| Location | Gate sidewall | In deep trenches on silicon substrate | Between or above polysilicon layers |
| Process Key | Anisotropic etching | Trenching, filling, CMP | Oxidation or deposition |

### Formulas

$$
\begin{equation}
\begin{aligned}
I_{ds}=
\begin{cases}
0 & V_{gs}<V_t \quad \text{Cutoff} \\
I_{dsat}\dfrac{V_{ds}}{V_{dsat}} = \beta(V_{GT} - \dfrac{V_{ds}}{2}) V_{ds} & V_{ds}<V_{dsat} \quad \text{Linear} \\
I_{dsat} = \dfrac{\beta}{2} V_{GT}^2  & V_{ds}>V_{dsat} \quad \text{Saturation}
\end{cases}
\end{aligned}
\end{equation}
$$

## FinFET

- $L \downarrow \xrightarrow{} R \uparrow$

- To enhance the **Gate Control over the channel** on voltage, we have **FinFET**

### Structure

1. FinFET

![](./imgs/Devices/FinFET.png)

- 2 sides of the gate are independent gates, **exerting different voltages**, which adjusts $V_t$ dynamicly

2. Fin

![](./imgs/Devices/Fin.png)

3. FinFET-Width

![](./imgs/Devices/FinFET-Width.png)

## GAAFET

## Transistor Functions

### Gates

1. Basic Logic for constructing logic gates using CMOS

| Network | Transistor Type | Implemented Logic | Series Connection | Parallel Connection |
|---|---|---|---|---|
| Pull-Down Network (PDN) | NMOS | Function F | AND | OR |
| Pull-Up Network (PUN) | PMOS | Dual of PDN structure | OR | AND |

2. Gates

| Gate Type | Description |
|---|---|
| Pass Transistor / Transmission Gates | Allow signal passage when enabled, acting as a switch. Transmission gates use parallel NMOS and PMOS for better signal integrity (strong '0' and '1'). |
| Restoring Gate | Regenerates logic levels, driving output strongly to $V_{DD}$ or $GND$ to prevent signal degradation. |

# Diodes

## Shockley Diode

$$
\begin{equation}
\begin{aligned}
I = I_S (e^{\dfrac{V_D}{nV_T}} - 1)
\end{aligned}
\end{equation}
$$

| Symbol | Description |
|---|---|
| $n$ | Quality factor: 1 (ideal) - 2 |
| $V_T$ | Thermal Voltage ($V_T = \dfrac{kT}{q}$) |
| $V_D$ | Diode voltage |
