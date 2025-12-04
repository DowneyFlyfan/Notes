---
id: Combinational_Logic
aliases: []
tags:
  - Circuit
---

# RLC Circuits

1. Capacitance

$$
\begin{equation}
\begin{aligned}
C &= \frac{Q}{V} = I \frac{dV}{dt} \\
&= \frac{\epsilon A}{d} \\
X_c &= \frac{1}{\omega C}
\end{aligned}
\end{equation}
$$

2. Inductors

$$
\begin{equation}
\begin{aligned}
L &= \frac{N\Phi}{I} = -V \frac{dt}{dI} \\
&= \frac{\mu N^2 A}{l} \\
X_L &= \omega L
\end{aligned}
\end{equation}
$$

3. Resistance of Transistors

$$
\begin{equation}
\begin{aligned}
R &= \frac{V}{I} \\
&= \frac{\rho L}{A} \\
&= \frac{1}{k_n (V_{GS} - V_{th})} \\
k_n &= \mu_n C_{ox} \frac{W}{L} 
\end{aligned}
\end{equation}
$$

- It sometimes is also refered as **electrical resistivity** $\rho(\Omega \cdot m)$ or **Resistance per ..** $\Omega / m$

# Boolean Logic

## Duality

$$
\begin{equation}
\begin{aligned}
F'(X) &= F(X')
\end{aligned}
\end{equation}
$$

## XOR

### Basics

$$
\begin{equation}
\begin{aligned}
A \oplus 1 &= A' \\
A \oplus 0 &= A \\
A \oplus A &= 0 \\
A \oplus A' &= 1
\end{aligned}
\end{equation}
$$

### Inversion Law

$$
\begin{equation}
\begin{aligned}
\bigoplus_{i=1}^{n_{\text{odd}}} \overline{x_i} &= \overline{\bigoplus_{i=1}^{n_{\text{odd}}} x_i} \\
\bigoplus_{i=1}^{n_{\text{even}}} \overline{x_i} &= \bigoplus_{i=1}^{n_{\text{even}}} x_i \\
\end{aligned}
\end{equation}
$$

# Adder

- 所有的$t_{FA}$指的都是**Single-Bit FA**的时间

