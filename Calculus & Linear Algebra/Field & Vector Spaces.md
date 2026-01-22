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

## Canonical Examples of Defining a Vector Space

### Standard

> Give a Field $\mathcal{F}$, $n$ is an postive integar , A vector space can be defined as

$$
\begin{equation}
\begin{aligned}
\mathbf{F} ^n &= \big\{ \begin{bmatrix}
x_1 \\
x_2 \\
... \\
x_n 
\end{bmatrix}, x_i \in \mathcal{F} \big\}
\end{aligned}
\end{equation}
$$

> Addition

$$
\begin{equation}
\begin{aligned}
\begin{bmatrix}
x_1 \\
x_2 \\
... \\
x_n
\end{bmatrix} + \begin{bmatrix}
y_1 \\
y_2 \\
... \\
y_n
\end{bmatrix} &\triangleq  \begin{bmatrix}
x_1 + y_1 \\
x_2 + y_2 \\
... \\
x_n + y_n 
\end{bmatrix}, x_i, y_i \in \mathcal{F} 
\end{aligned}
\end{equation}
$$

> Multiplication

$$
\begin{equation}
\begin{aligned}
\alpha  \begin{bmatrix}
x_1 \\
x_2 \\
... \\
x_n
\end{bmatrix} &=
\begin{bmatrix}
\alpha x_1 \\
\alpha x_2 \\
... \\
\alpha x_n
\end{bmatrix}, \alpha, x_i \in \mathcal{F} 
\end{aligned}
\end{equation}
$$

### Function Space

$$
\begin{equation}
\begin{aligned}
\mathcal{V}&: \big\{ f: \mathcal{R} \xrightarrow{} \mathcal{R} \big\} \\
(f_1 + f_2)(x) &= f_1(x) + f_2(x), +: \textbf{Real Addition} \\
(\alpha f)(x) &= \alpha f(x), \alpha \in \mathcal{F} 
\end{aligned}
\end{equation}
$$

### Table Definition (Define its add & mult !!!)

$$
\begin{equation}
\begin{aligned}
\mathbb{F}^{m \times n} &= \begin{bmatrix}
x_{11} & ... & x_{1n} \\
.. & .. & .. \\
x_{m1} & .. & x_{mn}
\end{bmatrix}, x_{ij} \in \mathcal{F} 
\end{aligned}
\end{equation}
$$

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

- $\mathcal{U}+\mathcal{W}$ is also a subspace if $\mathcal{U}, \mathcal{W}$ are subspaces

- $\mathcal{V} = \mathcal{U} \cap \mathcal{W}$ is also a subspace (All elements are in both spaces, satisfying subspace definition on both side)

- $\mathcal{V} = \mathcal{U} \cup \mathcal{W}$ is not always a subspace

### Number of Types of subspace for $\mathcal{R}^n$

- $n+1$ (0 set)

### Line can be only formed in a infinite set Field

> Proof that finite set field can not form a line

$$
\begin{equation}
\begin{aligned}
\mathcal{L}_{v_0} &= \big\{ \alpha v_0 , \alpha \in \mathcal{F} \big\} \\
\mathcal{F} &= \big\{ 0, 1 \big\} \\
v_0 &= [1,1] \xRightarrow{}  \mathcal{L}_{v_0} = \big\{ [0,0], [1,1] \big\}
\end{aligned}
\end{equation}
$$

## Span

- Span is a subspace

$$
\begin{equation}
\begin{aligned}
span \big\{ u_1, ... u_k \big\}
\end{aligned}
\end{equation}
$$

- 

## Column/Row Space, NullSpace

> For $A \subseteq \mathcal{F}^{m \times n}$

$$
\begin{equation}
\begin{aligned}
\mathcal{R}(A) &= \big\{ y \in \mathcal{F^m}, \text{s.t. there exists a }  y = Ax, x \in \mathcal{F^n} \big\} \\
\mathcal{N} (A) &= \big\{  x, x\in \mathcal{F}^n \text{ s.t.} Ax = 0 \big\} = \mathcal{C} (A^T)^T
\end{aligned}
\end{equation}
$$

- $\mathcal{R(A)}$ is a subspace of $F^m$ (**proof**), called Column Space (Range)
