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
| Laws | Commutative, associative, distributive laws |
| Multiplicative Identity | There exists $1$ such that $x \cdot 1 = x$ for all $x \in \mathcal{F}$ |
| Additive Identity | There exists $0$ such that $x + 0 = x$ for all $x \in \mathcal{F}$ |
| Multiplicative Inverse | For each $x \in \mathcal{F}$ with $x \neq 0$, there exists $x^{-1}$ such that $x \cdot x^{-1} = 1$ |
| Additive Inverse | For each $x \in \mathcal{F}$, there exists $-x$ such that $x + (-x) = 0$ |
| Closure under Addition | $x + y \in \mathcal{F}$ for all $x, y \in \mathcal{F}$ |
| Closure under Multiplication | $x \cdot y \in \mathcal{F}$ for all $x, y \in \mathcal{F}$ |


## Axioms and Special Fields

| Property | Description |
| :--- | :--- |
| Uniqueness | $1,0, x^{-1},x_I$ are unique |
| Zero and Identity Multiplication | $0 \cdot a = 0, 1_I \cdot a = a_I$ |
| Binary Field (GF₂) | $\mathcal{F} = \{0,1\}$ |
| Complex Field | $(x,y) + (p,q) = (x+p, y + q)$ <br> $(x,y) \cdot (p,q) = (xp - yq, xq + yp)$ |

# Vector Spaces

## Definition

> Vector Spaces $\mathcal{V}$ is **a set** defined on a field $\mathcal{F}$, which satisfies

| Property | Condition |
| :--- | :--- |
| Identities & Inverses | $1,0,x_I$ same as in $\mathcal{F}$ |
| Laws | Commutative, distributive and associativity laws |
| Operations | Scalar multiplication $\cdot$ and vector addition $+$ |
| Closure under Addition | $x + y \in \mathcal{V}, \forall x, y \in \mathcal{V}$ |
| Closure under Scalar Mult | $\alpha x \in \mathcal{V}, \forall \alpha \in \mathcal{F}, \forall x \in \mathcal{V}$ |

## Vector Subspace

### Definition

> $W \subseteq V$ if $W$ satisfy

$$
\begin{equation}
\begin{aligned}
u + v &\in W, u, v \in W \\
\alpha u &\in W, u \in W, \alpha \in \mathcal{F} 
\end{aligned}
\end{equation}
$$

### Properties

| Property | Description |
| :--- | :--- |
| Sum | $\mathcal{U}+\mathcal{W}$ is also a subspace if $\mathcal{U}, \mathcal{W}$ are subspaces |
| Intersection | $\mathcal{V} = \mathcal{U} \cap \mathcal{W}$ is also a subspace (All elements are in both spaces, satisfying subspace definition on both side) |
| Union | $\mathcal{V} = \mathcal{U} \cup \mathcal{W}$ is a subspace **iff** $\mathcal{U} \subseteq \mathcal{W}$ or $\mathcal{W} \subseteq \mathcal{U}$ |

## Column(Range)Space, NullSpace, Linear Independence

> For $A \subseteq \mathcal{F}^{m \times n}$

| Space | Definition | Description |
| :--- | :--- | :--- |
| **Column Space (Range)** | $\mathcal{Col}(A) = \mathcal{R}(A) = \{ y \in \mathcal{F}^m \mid \exists x \in \mathcal{F}^n, y = Ax \}$ | Subspace of $\mathcal{F}^m$ (**proof**) |
| **Null Space** | $\mathcal{N}(A) = \{ x \in \mathcal{F}^n \mid Ax = 0 \}$ | Subspace of $\mathcal{F}^n$ |

$$
\begin{equation}
\begin{aligned}
span \big\{ u_1, ... u_k \big\} &= \mathcal{R} (A) \\
A^{n \times k} &= [u_1, u_2,...u_k]
\end{aligned}
\end{equation}
$$

> A set of vectors is linearly independent if the only coefficients that make their linear combination equal to zero are all zero.

- Any vector in the span of a linearly independent set has a **unique representation**

## Basis

> A basis for a vector space $\mathcal{V}$ is a set of vectors $\{v_1, v_2, ..., v_n\}$ that satisfies two conditions:

1. **Spanning**: $\text{span}\{v_1, v_2, ..., v_n\} = \mathcal{V}$

2. **Linear Independence**: The vectors $v_1, v_2, ..., v_n$ are linearly independent

- Note that $dim(\mathcal{V}) = n$
