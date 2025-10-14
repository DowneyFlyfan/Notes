---
id: Electronic_Devices
aliases: []
tags:
  - Circuit
---

# Transistors

## CMOS (Metal-Oxide-Semiconductor)

### Structure

![](./imgs/Devices/NMOS.png)

| Feature | Nitride Spacer | Shallow Trench Isolation (STI) | Poly Oxide |
|---|---|---|---|
| Main Function | Sidewall mask, defines LDD | Electrical isolation of devices | Interlayer dielectric (in floating-gate memory) |
| Main Material | Si$_{3}$N$_{4}$ | SiO$_{2}$ | SiO$_{2}$ |
| Location | Gate sidewall | In deep trenches on silicon substrate | Between or above polysilicon layers |
| Process Key | Anisotropic etching | Trenching, filling, CMP | Oxidation or deposition |


### Why does NMOS has higher conductivity compared with PMOS

NMOS (N-type Metal-Oxide-Semiconductor) transistors have higher conductivity compared to PMOS (P-type Metal-Oxide-Semiconductor) transistors primarily due to the difference in carrier mobility.

- **Carrier Type**: NMOS transistors use electrons as charge carriers, while PMOS transistors use holes.

- **Carrier Mobility**: Electrons in silicon have higher mobility than holes.

- **Impact on Current**: Since current is directly proportional to carrier mobility (I = nqµEA, where n is carrier concentration, q is charge, µ is mobility, E is electric field, and A is cross-sectional area), higher electron mobility in NMOS devices leads to a larger current for a given applied voltage and device geometry. This translates to higher conductivity.

2. Source and Drain are **identical**

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

## Shockley Equation

The Shockley diode equation is a fundamental model that describes the current-voltage relationship in p-n junction diodes, crucial for understanding their behavior in electronic circuits.

The Shockley diode equation is a fundamental model that describes the current-voltage relationship in p-n junction diodes, crucial for understanding their behavior in electronic circuits.

**Definition:** The Shockley diode equation models the current-voltage (I-V) characteristic of an ideal p-n junction diode in either forward or reverse bias.

**Formula:** The Shockley diode equation is given by:

$$
I = I_S \left( e^{\frac{V_D}{n V_T}} - 1 \right)
$$

Where:
*   $I$: Diode current
*   $I_S$: Reverse saturation current (or scale current), constant for a given temperature and diode.
*   $V_D$: Voltage across the diode (positive for forward bias, negative for reverse bias).
*   $n$: Ideality factor (or quality factor), typically ranging from 1 to 2, depending on the fabrication process and material.
*   $V_T$: Thermal voltage.

**Thermal Voltage ($V_T$):**

$$
V_T = \frac{kT}{q}
$$

Where:
*   $k$: Boltzmann's constant ($1.38 \times 10^{-23}$ J/K)
*   $T$: Absolute temperature in Kelvin
*   $q$: Magnitude of the elementary charge ($1.602 \times 10^{-19}$ C)

### Induction (Simplified)

The Shockley diode equation can be derived by considering the movement of charge carriers (electrons and holes) across the p-n junction under different biasing conditions:

1.  **Carrier Movement:** In a p-n junction, current is due to both drift (movement under electric field) and diffusion (movement from high to low concentration) of charge carriers.

2.  **Equilibrium (No Bias, $V_D = 0$):** At thermal equilibrium, the diffusion current of majority carriers (e.g., holes from p-side to n-side) is exactly balanced by the drift current of minority carriers (e.g., thermally generated holes in the n-side drifting to the p-side). The net current is zero.

3.  **Forward Bias ($V_D > 0$):**
    *   An applied forward voltage reduces the potential barrier across the depletion region.
    *   This reduction allows a significant increase in the diffusion of majority carriers across the junction.
    *   The diffusion current increases exponentially with the forward voltage.
    *   The drift current (reverse saturation current) remains relatively constant, as it primarily depends on thermal generation, which is less affected by the applied voltage.
    *   The net current is dominated by this increased diffusion current.

4.  **Reverse Bias ($V_D < 0$):**
    *   An applied reverse voltage increases the potential barrier.
    *   This almost completely stops the diffusion of majority carriers.
    *   The only significant current is the small, constant reverse saturation current, which is due to the drift of thermally generated minority carriers across the junction.

5.  **Mathematical Basis:** The exponential term in the Shockley equation arises from the exponential relationship between the applied voltage and the excess minority carrier concentration at the edges of the depletion region. By integrating the diffusion current equations and summing the contributions from both electron and hole currents, the Shockley equation can be derived. The "-1" term accounts for the reverse saturation current, ensuring that when no voltage is applied ($V_D = 0$), the net current is zero.
