---
id: Least_Sqaure_Estimators
aliases: []
tags: []
---

# Ordinary Least Squares Estimators

$$
\begin{equation}
\begin{aligned}
\mathbf{y} &= \mathbf{X}\beta + \epsilon
\end{aligned}
\end{equation}
$$

- $\mathbf{y} \in \mathbb{R}^{n \times 1}$ is the observation vector
- $\mathbf{X} \in \mathbb{R}^{n \times p}$ is the design matrix
- $\beta \in \mathbb{R}^{p \times 1}$ is the parameter vector to be estimated
- $\epsilon \in \mathbb{R}^{n \times 1}$ is the error vector

The objective is to minimize the sum of squared residuals $S(\beta)$:

$$
\begin{equation}
\begin{aligned}
S(\beta) &= \sum_{i=1}^n (y_i - \mathbf{x}_i^T \beta)^2 = (\mathbf{y} - \mathbf{X}\beta)^T (\mathbf{y} - \mathbf{X}\beta) \\
&= (\mathbf{y}^T - \beta^T \mathbf{X}^T) (\mathbf{y} - \mathbf{X}\beta) \\
&= \mathbf{y}^T \mathbf{y} - \mathbf{y}^T \mathbf{X}\beta - \beta^T \mathbf{X}^T \mathbf{y} + \beta^T \mathbf{X}^T \mathbf{X}\beta
\end{aligned}
\end{equation}
$$

Since $\mathbf{y}^T \mathbf{X}\beta$ and $\beta^T \mathbf{X}^T \mathbf{y}$ are scalars, and $(\mathbf{y}^T \mathbf{X}\beta)^T = \beta^T \mathbf{X}^T \mathbf{y}$, we have:

$$
\begin{aligned}
\mathbf{y}^T \mathbf{X}\beta &= \beta^T \mathbf{X}^T \mathbf{y} \\
S(\beta) &= \mathbf{y}^T \mathbf{y} - 2\beta^T \mathbf{X}^T \mathbf{y} + \beta^T \mathbf{X}^T \mathbf{X}\beta
\end{aligned}
$$

To find the $\beta$ that minimizes $S(\beta)$, we take the partial derivative with respect to $\beta$ and set it equal to the zero vector:

$$
\begin{equation}
\begin{aligned}
\frac{\partial S(\beta)}{\partial \beta} &= \frac{\partial}{\partial \beta} (\mathbf{y}^T \mathbf{y} - 2\beta^T \mathbf{X}^T \mathbf{y} + \beta^T \mathbf{X}^T \mathbf{X}\beta) \\
&= 0 - 2\mathbf{X}^T \mathbf{y} + 2\mathbf{X}^T \mathbf{X}\beta \\
&= -2\mathbf{X}^T \mathbf{y} + 2\mathbf{X}^T \mathbf{X}\beta \\
-2\mathbf{X}^T \mathbf{y} + 2\mathbf{X}^T \mathbf{X}\beta &= 0 \\
2\mathbf{X}^T \mathbf{X}\beta &= 2\mathbf{X}^T \mathbf{y} \\
\mathbf{X}^T \mathbf{X}\beta &= \mathbf{X}^T \mathbf{y}
\end{aligned}
\end{equation}
$$

If $(\mathbf{X}^T \mathbf{X})$ is invertible, we can solve for $\beta$:

$$
\begin{equation}
\begin{aligned}
\hat{\beta} &= (\mathbf{X}^T \mathbf{X})^{-1} \mathbf{X}^T \mathbf{y}
\end{aligned}
\end{equation}
$$
