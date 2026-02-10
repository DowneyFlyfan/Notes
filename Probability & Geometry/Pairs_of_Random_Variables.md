---
id: Multi-Variables
aliases: []
tags:
  - Math
---

> Rectangular Inequality
For any $x_1 < x_2$ and $y_1 < y_2$, the probability that the random variables $(X, Y)$ fall within the rectangle $(x_1, x_2] \times (y_1, y_2]$ is given by:

$$
\begin{equation}
\begin{aligned}
\Delta &= P(x_1 < X \le x_2, y_1 < Y \le y_2) \\
&= F_{X,Y}(x_2, y_2) - F_{X,Y}(x_1, y_2) - F_{X,Y}(x_2, y_1) + F_{X,Y}(x_1, y_1) \\
&\ge 0
\end{aligned}
\end{equation}
$$

> joint -> marginal (F, f)

> Conditional probability (Chain Rule)

> Conditional Independance

> Positive Semidefinite (Generalization of Positive in Matrix)

> Covariance Matrix

> Sum of Multi-Variables: E = sum E, Var = sum of elements in Covariance Matrix

> Markov Chain

$$
\begin{equation}
\begin{aligned}
P(X_{n+1} &= j \mid X_n = i, X_{n-1} = i_{n-1}, \dots, X_0 = i_0) = P(X_{n+1} = j \mid X_n = i) = p_{ij} \\
p_{ij} &\ge 0 \quad \text{and} \quad \sum_{j \in S} p_{ij} = 1
\end{aligned}
\end{equation}
$$

- A Markov chain is a stochastic process where the future state depends only on the current state, not on the sequence of events that preceded it (Markov property).

- Where $p_{ij}$ is the transition probability from state $i$ to state $j$

- The transition matrix $P = [p_{ij}]$ contains all transition probabilities

> Q-function

$$
\begin{equation}
\begin{aligned}
Q(x) &= F_X(X \gt x) = \int_{x}^{\infty } \frac{1}{\sqrt{2 \pi}} e^{-\dfrac{u^2}{2} } du = 1 - \Phi(x)
\end{aligned}
\end{equation}
$$
