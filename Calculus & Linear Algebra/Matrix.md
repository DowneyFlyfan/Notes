---
id: Matrix
aliases: []
tags:
  - Math
---
# Matrix Basics

## Matrix Properties

- **Associativity of Multiplication**: $(AB)C = A(BC)$

$$
\begin{equation}
\begin{aligned}
T : \mathcal{U} \xrightarrow{} \mathcal{V}, det(U) &\lt \infty \\
dim(\mathcal{R} (T)) + dim(\mathcal{N} (T)) &= dim(\mathcal{\mathcal{U} } )
\end{aligned}
\end{equation}
$$

- $if \mathcal{N} (T) = \mathcal{U}$: ???

## Vector Op & Linear map

> Linear transformations map lines to lines (or points) and keep grid lines parallel and evenly spaced.

| Operation | Formula | Geometric Interpretation |
| :--- | :--- | :--- |
| **Dot Product** ($\cdot$) | $\vec{\pmb{v}} \cdot \vec{\pmb{w}} = \sum v_i w_i = \vec{\pmb{v}}^T \vec{\pmb{w}} = \|\vec{\pmb{v}}\| \|\vec{\pmb{w}}\| \cos \theta$ | Projection of $\vec{\pmb{v}}$ onto $\vec{\pmb{w}}$ is $\frac{\vec{\pmb{v}} \cdot \vec{\pmb{w}}}{\|\vec{\pmb{w}}\|^2} \vec{\pmb{w}}$. |
| **Cross Product** ($\times$) | $\|\vec{\pmb{v}} \times \vec{\pmb{w}}\| = \|\vec{\pmb{v}}\| \|\vec{\pmb{w}}\| \sin \theta$ | Area of parallelogram. Direction is $\perp$ to the plane. |
| **Linear Map** | $f(x) = A \pmb{x}$ | $f: \mathcal{F}^n \to \mathcal{F}^m$ maps lines to lines and keeps grid lines parallel and evenly spaced. |

## Examples of Linear Operators

| Operator | Formula | Description |
| :--- | :--- | :--- |
| **Derivative** | $D \begin{bmatrix} a_0 \ a_1 \ a_2 \end{bmatrix} = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 2 \\ 0 & 0 & 0 \end{bmatrix} \begin{bmatrix} a_0 \ a_1 \ a_2 \end{bmatrix}$ | Differentiation of polynomials. |
| **Orthogonal Transformation** | $T(\vec{\pmb{v}}) \cdot T(\vec{\pmb{w}}) = \vec{\pmb{v}} \cdot \vec{\pmb{w}}$ | Preserves dot products (e.g., Reflection, Rotation). |

## Subspace & Rank

> For a matrix $A \in \mathcal{R}^{m \times n}$:

| Subspace / Property | Description | Definition / Formula |
| :--- | :--- | :--- |
| **Column Space**, $Col(A), R(A)$ | The column space of $A$ is the span of its column vectors. It's a subspace of $\mathcal{R}^m$. | $Col(A) = \{ A\vec{\pmb{x}} \mid \vec{\pmb{x}} \in \mathcal{R}^n \}$ |
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

# Determinant, Trace

## Determinant

> Scalar for square matrix $A$, denoted $\det(A)$ or $|A|$.

$$ \det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^n a_{i, \sigma(i)} $$

| Property | Formula / Condition |
| :--- | :--- |
| **Multiplication** | $\det(AB) = \det(A)\det(B)$ |
| **Transpose** | $\det(A^T) = \det(A)$ |
| **Inverse** | $\det(A^{-1}) = 1/\det(A)$ (if $A$ is invertible) |
| **Invertibility** | $A$ is invertible if and only if $\det(A) \neq 0$ |
| **Rank** | If $\det(A) = 0$, not full rank |

## Trace

| Property | Formula |
| :--- | :--- |
| **Definition** | $Tr(A) = \sum_{i=1}^{n} A_{ii}$ |
| **Cyclic Property** | $Tr(AB) = Tr(BA)$ |
| **Summation Form** | $\sum_{i}^{} \sum_{j}^{} a_{ij} b_{ji} = \sum_{i}^{} \sum_{j}^{} a_{ji} b_{ij}$ |

## Cramer's Rule

For $A\vec{\pmb{x}} = \vec{\pmb{b}}$ (invertible $A$):

$$ x_i = \frac{\det(A_i)}{\det(A)} $$

where $A_i$ is $A$ with its $i$-th column replaced by $\vec{\pmb{b}}$.

# Special Types of Matrices

| Matrix Type          | Definition                                                                  | Properties                                                                             |
| :------------------- | :-------------------------------------------------------------------------- | :------------------------------------------------------------------------------------- |
| **Singular Matrix**  | A square matrix whose determinant is zero, or whose columns (and rows) are linearly dependent (space is compressed). | $\det(A) = 0$                                                                          |
| **Inverse Matrix** ($A^{-1}$) | For a square matrix $A$, its inverse $A^{-1}$ (if it exists) is a matrix such that $AA^{-1} = A^{-1}A = I$ (Identity matrix). | A matrix is invertible if and only if its determinant is non-zero.<br>- $(A^{-1})^{-1} = A$<br>- $(AB)^{-1} = B^{-1}A^{-1}$<br>- $(kA)^{-1} = \frac{1}{k}A^{-1}$ (for non-zero scalar $k$)<br>- $(A^T)^{-1} = (A^{-1})^T$<br>- Used to solve linear systems: If $A\vec{\pmb{x}} = \vec{\pmb{b}}$ and $A$ is invertible, then $\vec{\pmb{x}} = A^{-1}\vec{\pmb{b}}$. |
| **Transpose Matrix** ($A^T$) | The transpose $A^T$ of a matrix $A$ is obtained by swapping its rows and columns. | - $(A^T)^T = A$<br>- $(A+B)^T = A^T + B^T$<br>- $(kA)^T = kA^T$<br>- $(AB)^T = B^TA^T$<br>- $AA^T$ and $A^TA$ are always symmetric matrices. |
| **Symmetric Matrix** | A square matrix $A$ is symmetric if $A = A^T$.                             | - $A = A^T$                                                                            |
| **Orthogonal Matrix** | A square matrix $A$ is orthogonal if its columns (and rows) are orthonormal vectors. | - $A^T A = A A^T = I$- $A^{-1} = A^T$, 正交矩阵表示rotation或者reflection|
| **Diagonal Matrix**  | A square matrix where all off-diagonal elements are zero | $A_{ij} = 0$ for $i \neq j$.                                                     |
|**Augmented Matrix**| $Ax = B \xRightarrow{}, [A\|B]$ is the augmented matrix| $rank(A) < rank(A\|B)$, the system has no solution; $rank(A) = rank(A\|B) = n$, the system has a unique solution; $rank(A) = rank(A\|B) > n$, the system has infinitely many solutions  |

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

> For **diagonalizable** $A \in \mathcal{R}^{n \times n}$:

$$
\begin{equation}
\begin{aligned}
A x_i &= \lambda_i x_i \\
P &= [x_1, ... x_n] \\
D &= [ \lambda_1, ... \lambda_n] \\
AP &= [ \lambda_0 x_0, \lambda_1 x_1, ... \lambda_n x_n ] \\
&= PD
\end{aligned}
\end{equation}
$$

> Decomposition & Diagonal Matrix

$$
\begin{equation}
\begin{aligned}
A &= \begin{cases}
PDP^{-1} & Normal  \\
PDP^T & \text{A is real symmetric matrix}
\end{cases} \\
D &= PAP^{-1} = P^{-1} A P
\end{aligned}
\end{equation}
$$

## Singular Value Decomposition (SVD)

Any matrix $A \in \mathcal{R}^{m \times n}$ can be decomposed as:
$$
\begin{equation}
\begin{aligned}
A &= U \Sigma V^T \\
\sigma_i &= \sqrt{\lambda_i}
\end{aligned}
\end{equation}
$$
| Symbol | Dimensions | Description |
| :--- | :--- | :--- |
| $U$ | $\mathcal{R}^{m \times m}$ | Orthogonal matrix whose columns are the left singular vectors (eigenvectors of $AA^T$) |
| $\Sigma$ | $\mathcal{R}^{m \times n}$ | Diagonal matrix with non-negative real numbers called singular values on its diagonal |
| $V$ | $\mathcal{R}^{n \times n}$ | Orthogonal matrix whose columns are the right singular vectors (eigenvectors of $A^TA$) |

# Matrix Derivatives

## Basic Formulas

1. $\dfrac{\partial (\mathbf{a}^T \mathbf{x})}{\partial \mathbf{x}} = \mathbf{a}$

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

2. $\dfrac{\partial (\mathbf{x}^T \mathbf{A}\mathbf{x})}{\partial \mathbf{x}} = (\mathbf{A} + \mathbf{A}^T)\mathbf{x}$

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

- Therefore

$$
\begin{equation}
\begin{aligned}
\frac{\partial (\mathbf{x}^T \mathbf{A}\mathbf{x})}{\partial \mathbf{x}} &= (\mathbf{A} + \mathbf{A}^T)\mathbf{x}
\end{aligned}
\end{equation}
$$
