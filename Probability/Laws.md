---
id: Laws
aliases: []
tags:
  - Math
---

# Inequalities

## Markov Inequalities

- For $X \ge 0$

$$
\begin{equation}
\begin{aligned}
E(X) &= \int_{0}^{a} xf(x) dx + \int_{a}^{\infty } xf(x) dx \\
&\ge \int_{a}^{\infty } xf(x) dx \\
&\ge \int_{a}^{\infty } af(x) dx  = aP(X \ge a) \\
\therefore  P(X \ge a) &\le  \frac{E(X)}{a} 
\end{aligned}
\end{equation}
$$

## Chebyshev's Inequalities

- Since $(X-\mu)^2 \ge 0$, Markov inequalities can be applied to following equation

$$
\begin{equation}
\begin{aligned}
P(|X - \mu| \ge a) &= P[ (X-\mu)^2 \ge a^2 ] \\
&\le \frac{E((X-\mu)^2)}{a^2}  \\
P(|X - \mu| \ge a)&\le\frac{\sigma^2}{a^2} 
\end{aligned}
\end{equation}
$$
