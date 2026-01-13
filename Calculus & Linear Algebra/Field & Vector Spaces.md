---
id: Space
aliases: []
tags:
  - Math
---

# Fields

## Definition

> A field is defined to satisfy certain properties

| Property | Condition |
| :--- | :--- |
| Laws | Commutative, associativity, distributive laws |
| Multiplicative Identity | There exists a $1$, s.t. $x \cdot 1 = x, \forall x \in \mathcal{F}$ |
| Additive Identity | There exists a $0$, s.t. $x + 0 = x, \forall x \in \mathcal{F}$ |
| Multiplicative Inverse | There exists a $x^{-1}$, s.t. $x \cdot x^{-1} = 1, \forall x \in \mathcal{F}, x \neq 0$ |
| Additive Inverse | There exists a $x_I$, s.t. $x + x_{I} = 0, \forall x \in \mathcal{F}$ |
| Closure | $x + y \in \mathcal{F}, x \cdot y \in \mathcal{F}, \forall x,y \in \mathcal{F}$ |

- **!!! Prove** the uniqueness of $1,0x^{-1},x_I$

## Special Fields

$$
\begin{equation}
\begin{aligned}
\mathcal{F} &: \big\{ 0,1 \big\}, \text{Binary}, GF_2  \\
\mathcal{F} &: (x,y) + (p,q) = (x+p, y + q) \\
& (x,y) \cdot (p,q) =(xp - yq, xq + yp), \text{Complex Field} 
\end{aligned}
\end{equation}
$$

# Vector Spaces

## Definition

> Vector Spaces $\mathcal{V}$ is **a set** defined on a field $\mathcal{F}$, which satisfies

| Property | Condition |
| :--- | :--- |
| Identities & Inverses | $1,0,x^{-1}, x_I$ same as in $\mathcal{F}$ |
| Laws | Commutative, distributive and associativity laws |
| Operations | Scalar multiplication $\cdot$ and vector addition $+$ |
| Closure under Addition | $x + y \in \mathcal{V}, \forall x, y \in \mathcal{V}$ |
| Closure under Scalar Mult | $\alpha x \in \mathcal{V}, \forall \alpha \in \mathcal{F}, \forall x \in \mathcal{V}$ |


