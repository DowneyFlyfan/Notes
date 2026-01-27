---
id: Basics for Linear Algebra
aliases: []
tags:
  - Math
---
# Matrix

## Associativity of Multiplication

| Property | Formula |
| :--- | :--- |
| **Associativity** | $(AB)C = A(BC)$ |

## Meaning of a Matrix

| Concept | Description | Formula |
| :--- | :--- | :--- |
| **Linear Transformation** | Any linear transformation $L: \mathcal{R}^n \to \mathcal{R}^m$ can be represented by an $m \times n$ matrix $A$ | $L(\vec{\pmb{x}}) = A\vec{\pmb{x}}$ |

## Vector Op & Linear Transformation

> Linear transformations map lines to lines (or points) and keep grid lines parallel and evenly spaced.

| Operation | Formula | Geometric Interpretation |
| :--- | :--- | :--- |
| **Dot Product** ($\cdot$) | $\vec{\pmb{v}} \cdot \vec{\pmb{w}} = \sum v_i w_i = \vec{\pmb{v}}^T \vec{\pmb{w}} = \|\vec{\pmb{v}}\| \|\vec{\pmb{w}}\| \cos \theta$ | Projection of $\vec{\pmb{v}}$ onto $\vec{\pmb{w}}$ is $\frac{\vec{\pmb{v}} \cdot \vec{\pmb{w}}}{\|\vec{\pmb{w}}\|^2} \vec{\pmb{w}}$. |
| **Cross Product** ($\times$) | $\|\vec{\pmb{v}} \times \vec{\pmb{w}}\| = \|\vec{\pmb{v}}\| \|\vec{\pmb{w}}\| \sin \theta$ | Area of parallelogram. Direction is $\perp$ to the plane. |
| **Linear Transformation** ($L$) | $L(\vec{\pmb{u}} + \vec{\pmb{v}}) = L(\vec{\pmb{u}}) + L(\vec{\pmb{v}})$ <br> $L(c\vec{\pmb{u}}) = cL(\vec{\pmb{u}})$ | $L: \mathcal{R}^n \to \mathcal{R}^m$ maps lines to lines and keeps grid lines parallel and evenly spaced. |

## Examples of Linear Operators

| Operator | Formula | Description |
| :--- | :--- | :--- |
| **Derivative** | $D \begin{bmatrix} a_0 \ a_1 \ a_2 \end{bmatrix} = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 2 \\ 0 & 0 & 0 \end{bmatrix} \begin{bmatrix} a_0 \ a_1 \ a_2 \end{bmatrix}$ | Differentiation of polynomials. |
| **Orthogonal Transformation** | $T(\vec{\pmb{v}}) \cdot T(\vec{\pmb{w}}) = \vec{\pmb{v}} \cdot \vec{\pmb{w}}$ | Preserves dot products (e.g., Reflection, Rotation). |

## Subspace & Rank

> For a matrix $A \in \mathcal{R}^{m \times n}$:

| Subspace / Property | Description | Definition / Formula |
| :--- | :--- | :--- |
| **Column Space** ($Col(A)$) | The column space of $A$ is the span of its column vectors. It's a subspace of $\mathcal{R}^m$. | $Col(A) = \{ A\vec{\pmb{x}} \mid \vec{\pmb{x}} \in \mathcal{R}^n \}$ |
| **Row Space** ($Row(A)$)   | The row space of $A$ is the span of its row vectors. It's a subspace of $\mathcal{R}^n$.    | $Row(A) = \{ \vec{\pmb{x}}^T A \mid \vec{\pmb{x}} \in \mathcal{R}^m \}$ |
| **Null Space** ($Null(A)$) | The null space (or kernel) of $A$ is the set of all vectors $\vec{\pmb{x}} \in \mathcal{R}^n$ such that $A\vec{\pmb{x}} = \vec{\pmb{0}}$. It's a subspace of $\mathcal{R}^n$. | The dimension of the null space is called the nullity of $A$, denoted $nullity(A)$. |
| **Rank**             | The rank of a matrix $A$, denoted $rank(A)$, is the dimension of its column space (which equals the dimension of its row space). It is the maximum number of linearly independent columns (or rows) of $A$. | $rank(A) \le \min(m, n)$ <br> $rank(A) = rank(A^T)$ <br> **Rank-Nullity Theorem**: $rank(A) + nullity(A) = n$ (where $n$ is the number of columns of $A$). |

## Eigenvalues and Eigenvectors

> For a square matrix $A \in \mathcal{R}^{n \times n}$:

| Concept | Description / Formula |
| :--- | :--- |
| **Definition** | $A\vec{\pmb{x}} = \lambda \vec{\pmb{x}}$ ($\vec{\pmb{x}} \neq \vec{\pmb{0}}$) |
| **Characteristic Eq** | $\det(A - \lambda I) = 0$ |
| **Properties** | $n$ eigenvalues; Geom mult $\le$ Alg mult; Diagonalizable iff $n$ independent eigenvectors. |
| **Interpretation** | Invariant directions where the transformation only scales the vector. |

# Determinants \& Trace

## Determinants

### Definition

- Scalar for square matrix $A$, denoted $\det(A)$ or $|A|$.

$$ \det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^n a_{i, \sigma(i)} $$

### Properties

| Property | Formula / Condition |
| :--- | :--- |
| **Multiplication** | $\det(AB) = \det(A)\det(B)$ |
| **Transpose** | $\det(A^T) = \det(A)$ |
| **Inverse** | $\det(A^{-1}) = 1/\det(A)$ (if $A$ is invertible) |
| **Invertibility** | $A$ is invertible if and only if $\det(A) \neq 0$ |
| **Rank** | If $\det(A) = 0$, not full rank |

## Trace

### Definition

$$
\begin{equation}
\begin{aligned}
Tr(A) &= \sum_{i=1}^{n} A_{ii}
\end{aligned}
\end{equation}
$$

### Properties

$$
\begin{equation}
\begin{aligned}
Tr(AB) &= Tr(BA) \\
\sum_{i}^{}  \sum_{j}^{}  a_{ij} b_{ji} &= \sum_{i}^{}  \sum_{j}^{}  a_{ji} b_{ij}
\end{aligned}
\end{equation}
$$

## Cramer's Rule

For a system of linear equations $A\vec{\pmb{x}} = \vec{\pmb{b}}$ where $A$ is an invertible $n \times n$ matrix, the $i$-th component of the solution $\vec{\pmb{x}}$ is given by:

$$
\begin{equation}
\begin{aligned}
x_i = \frac{\det(A_i)}{\det(A)}
\end{aligned}
\end{equation}
$$
where $A_i$ is the matrix $A$ with its $i$-th column replaced by $\vec{\pmb{b}}$.

# Special Types of Matrices

| Matrix Type          | Definition                                                                  | Properties                                                                             |
| :------------------- | :-------------------------------------------------------------------------- | :------------------------------------------------------------------------------------- |
| **Singular Matrix**  | A square matrix whose determinant is zero, or whose columns (and rows) are linearly dependent (space is compressed). | $\det(A) = 0$                                                                          |
| **Inverse Matrix** ($A^{-1}$) | For a square matrix $A$, its inverse $A^{-1}$ (if it exists) is a matrix such that $AA^{-1} = A^{-1}A = I$ (Identity matrix). | A matrix is invertible if and only if its determinant is non-zero.<br>- $(A^{-1})^{-1} = A$<br>- $(AB)^{-1} = B^{-1}A^{-1}$<br>- $(kA)^{-1} = \frac{1}{k}A^{-1}$ (for non-zero scalar $k$)<br>- $(A^T)^{-1} = (A^{-1})^T$<br>- Used to solve linear systems: If $A\vec{\pmb{x}} = \vec{\pmb{b}}$ and $A$ is invertible, then $\vec{\pmb{x}} = A^{-1}\vec{\pmb{b}}$. |
| **Transpose Matrix** ($A^T$) | The transpose $A^T$ of a matrix $A$ is obtained by swapping its rows and columns. | - $(A^T)^T = A$<br>- $(A+B)^T = A^T + B^T$<br>- $(kA)^T = kA^T$<br>- $(AB)^T = B^TA^T$<br>- $AA^T$ and $A^TA$ are always symmetric matrices. |
| **Symmetric Matrix** | A square matrix $A$ is symmetric if $A = A^T$.                             | - $A = A^T$                                                                            |
| **Orthogonal Matrix** | A square matrix $A$ is orthogonal if its columns (and rows) are orthonormal vectors. | - $A^T A = A A^T = I$- $A^{-1} = A^T$, 正交矩阵表示rotation或者reflection|
| **Diagonal Matrix**  | 非对角元素都为0的方阵 | $A_{ij} = 0$ for $i \neq j$.                                                     |
|**Augmented Matrix**| $Ax = B \xRightarrow{}, [A|B]$ 就是增广矩阵| $rank(A) < rank(A|B)$, 方程无解; $rank(A) = rank(A|B) = n$, 方程有1个解; $rank(A) = rank(A|B) > n$, 方程有无穷解  |

## Similar Matrices

Two square matrices $A$ and $B$ are similar if there exists an invertible matrix $P$ such that $B = PAP^{-1}$.

1. 代表**不同基下相同的线性变换**
2. Properties:

- They have the same eigenvalues: $\lambda_B = \lambda_A$.

-  If $\vec{\pmb{x}}_A$ is an eigenvector of $A$ for eigenvalue $\lambda$, then $\vec{\pmb{x}}_B = P\vec{\pmb{x}}_A$ is an eigenvector of $B$ for the same eigenvalue $\lambda$.

$$
\begin{equation}
\begin{aligned}
B \vec{\pmb{x}}_B &= (PAP^{-1})(P\vec{\pmb{x}}_A) \\
&= PA\vec{\pmb{x}}_A = P(\lambda \vec{\pmb{x}}_A) \\
&= \lambda (P\vec{\pmb{x}}_A) \\
&= \lambda \vec{\pmb{x}}_B
\end{aligned}
\end{equation}
$$

# Matrix Decompositions

## Spectral Decomposition (Eigen Decomposition)

- 对于**diagonalizable**($rank = n$)的方阵$A \in \mathcal{R}^{n \times n}$:

$$
\begin{equation}
\begin{aligned}
A x_i &= \lambda_i x_i \\
P &= [x_1, ... x_n] \\
D &= [ \lambda_1, ... \lambda_n] \\
AP &= [ \lambda_0 x_0, \lambda_1 x_1, ... \lambda_n x_n ] \\
&= PD \\
A &= PDP^{-1}
\end{aligned}
\end{equation}
$$

- 当$A$是实对称矩阵的时候

$$
\begin{equation}
\begin{aligned}
A &= PDP^T
\end{aligned}
\end{equation}
$$

## Singular Value Decomposition (SVD)

Any matrix $A \in \mathcal{R}^{m \times n}$ can be decomposed as:
$$
\begin{equation}
\begin{aligned}
A = U \Sigma V^T
\end{aligned}
\end{equation}
$$
where:
*   $U \in \mathcal{R}^{m \times m}$ is an orthogonal matrix whose columns are the left singular vectors (eigenvectors of $AA^T$).
*   $\Sigma \in \mathcal{R}^{m \times n}$ is a diagonal matrix with non-negative real numbers called singular values on its diagonal.
*   $V \in \mathcal{R}^{n \times n}$ is an orthogonal matrix whose columns are the right singular vectors (eigenvectors of $A^TA$).
The singular values $\sigma_i$ (diagonal entries of $\Sigma$) are the square roots of the non-zero eigenvalues of $A^TA$ (or $AA^T$).

# Matrix Derivatives

## Basic Formulas

1. $\frac{\partial (\mathbf{a}^T \mathbf{x})}{\partial \mathbf{x}} = \mathbf{a}$

$$
\begin{equation}
\begin{aligned}
\frac{\partial (\mathbf{a}^T \mathbf{x})}{\partial \mathbf{x}} &= 
\begin{pmatrix} \dfrac{\partial (\mathbf{a}^T \mathbf{x})}{\partial x_1} \ 
\dfrac{\partial (\mathbf{a}^T \mathbf{x})}{\partial x_2} \ 
\vdots \ 
\dfrac{\partial (\mathbf{a}^T \mathbf{x})}{\partial x_n} \end{pmatrix}
= \begin{pmatrix} a_1 \ a_2 \ \vdots \ a_n \end{pmatrix} 
= \mathbf{a}
\end{aligned}
\end{equation}
$$

2. $\frac{\partial (\mathbf{x}^T \mathbf{A}\mathbf{x})}{\partial \mathbf{x}} = (\mathbf{A} + \mathbf{A}^T)\mathbf{x}$

考虑一个标量函数 $f(\mathbf{x}) = \mathbf{x}^T \mathbf{A}\mathbf{x}$。我们想找到它对 $\mathbf{x}$ 的梯度。

$$
\begin{equation}
\begin{aligned}
f(\mathbf{x} + d\mathbf{x}) \approx f(\mathbf{x}) + \left( \frac{\partial f}{\partial \mathbf{x}} \right)^T d\mathbf{x}
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
f(\mathbf{x} + d\mathbf{x}) &= (\mathbf{x}^T + d\mathbf{x}^T) \mathbf{A}(\mathbf{x} + d\mathbf{x}) \\
&= \mathbf{x}^T \mathbf{A}\mathbf{x} + \mathbf{x}^T \mathbf{A}d\mathbf{x} + d\mathbf{x}^T \mathbf{A}\mathbf{x} + d\mathbf{x}^T \mathbf{A}d\mathbf{x} \\
&= \mathbf{x}^T \mathbf{A}\mathbf{x} + \mathbf{x}^T \mathbf{A}d\mathbf{x} + d\mathbf{x}^T \mathbf{A}\mathbf{x} \\
&=  f(\mathbf{x}) + d\mathbf{x}^T \mathbf{A}^T \mathbf{x} + d\mathbf{x}^T \mathbf{A}\mathbf{x} \\
&= f(\mathbf{x}) + d\mathbf{x}^T (\mathbf{A}^T + \mathbf{A})\mathbf{x} \\
&= f(\mathbf{x}) + ((\mathbf{A} + \mathbf{A}^T)\mathbf{x})^T d\mathbf{x}
\end{aligned}
\end{equation}
$$

比较以上公式可得

$$
\begin{equation}
\begin{aligned}
\frac{\partial (\mathbf{x}^T \mathbf{A}\mathbf{x})}{\partial \mathbf{x}} &= (\mathbf{A} + \mathbf{A}^T)\mathbf{x}
\end{aligned}
\end{equation}
$$
