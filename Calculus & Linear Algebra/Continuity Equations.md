---
id: Continuity Equations
aliases: []
tags: []
---

# Continuity Equations

- t: 时间, x: (高维)空间

## Euler Form

$$
\begin{aligned}
\text{Total amount of quantity } M_V(t) &= \int_V \rho(x, t) \, dV \\
\text{Rate of change of total amount: } \frac{dM_V}{dt} &= \int_V \frac{\partial \rho}{\partial t} (x, t) \, dV \\
\text{Net outflow through boundary: } \oint_{\partial V} J(x, t) \cdot \mathbf{n} \, dS &= \int_V \text{div}(J(x, t)) \, dV  \\
\text{Conservation Law: } \frac{dM_V}{dt} &= - \oint_{\partial V} J(x, t) \cdot \mathbf{n} \, dS \\
\Rightarrow \int_V \frac{\partial \rho}{\partial t} (x, t) \, dV &= - \int_V \text{div}(J(x, t)) \, dV \\
\Rightarrow \int_V \left( \frac{\partial \rho}{\partial t} (x, t) + \text{div}(J(x, t)) \right) \, dV &= 0 \\
\frac{\partial \rho}{\partial t} (x, t) + \text{div}(J(x, t)) &= 0 \\
\frac{\partial \rho}{\partial t} (x, t) + \text{div}(\rho(x, t) v(x, t)) &= 0
\end{aligned}
$$

## Log Form

$$
\begin{equation}
\begin{aligned}
\frac{d \phi_t(x)}{dt} &= \pmb v[\phi_t(x)]  \\
\frac{\partial }{\partial  t} [ \log p_t(\phi_t(x))] \large|_{y = \phi_t(x)}\
&= \frac{1}{p_t(y)} \big[ \frac{dp_t(y)}{dt} + \frac{dp_t(y)}{dy} \frac{dy}{dt}  \big] \\
&= \frac{1}{p_t(y)}  \big[ - \nabla  p_t(y) \pmb v_t(y) - \nabla \pmb v_t(y) p_t(y) + \nabla  p_t(y) \pmb v_t(y) \big] \\
&= -\nabla \pmb v_t(y) \\
\frac{\partial }{\partial t} [ \log p_t(\phi_t(x))] &= -\nabla \pmb v_t(\phi_t(x))
\end{aligned}
\end{equation}
$$
