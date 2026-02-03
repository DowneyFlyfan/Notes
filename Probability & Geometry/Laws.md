---
id: Laws
aliases: []
tags:
  - Math
---

# Inequalities

## Markov Inequalities

### Definition & Proof

- For $X \ge 0$

> Proof

$$
\begin{equation}
\begin{aligned}
E(X) &= \int_{0}^{a} xf(x) dx + \int_{a}^{\infty } xf(x) dx \\
&\ge \int_{a}^{\infty } xf(x) dx \\
&\ge \int_{a}^{\infty } af(x) dx  = aP(X \ge a) \\
\therefore  P(X \ge a) &\le  \frac{E(X)}{a}  \\

\end{aligned}
\end{equation}
$$

> Proof Using Total Expectation

$$
\begin{equation}
\begin{aligned}
E(X) &\ge E(X | X \ge a) P(X \ge a) \\
&\ge a P(X\ge a) \\
\therefore  P(X \ge a) &\le  \frac{E(X)}{a}
\end{aligned}
\end{equation}
$$

> Deductions

$$
\begin{equation}
\begin{aligned}
P( X \ge a \mu) &\le \frac{1}{a} \\
P(X \lt a) \gt 1 - \frac{\mu}{a} \\
P(X \in [0, a)) \gt 1 - \frac{\mu}{a} \\
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
P(|X - \mu| \ge a)&\le \frac{\sigma^2}{a^2}  \\
P(|X - \mu| \lt a)&\ge 1 - \frac{\sigma^2}{a^2}
\end{aligned}
\end{equation}
$$

# Weak Law of Large Numbers(WLLN) & Central Limit Theorem (CTL)

## Samples, Events

> Expectation of Sample Mean is distribution's Expectation

$$
\begin{equation}
\begin{aligned}
E(\widehat{X_n} ) &= E(X) \\
V(\widehat{X_n} ) &= \frac{1}{n} \sum_{i=1}^{n} \Big( Var(X_i) \Big) \\
&= \frac{1}{n^2}  (n \sigma ^2) \\
&= \frac{\sigma^2 }{n}
\end{aligned}
\end{equation}
$$

> Event Probability using indicator method

$$
\begin{equation}
\begin{aligned}
\frac{1}{n} \sum_{i=1}^{n}  \mathcal{I}_i(X_i) &= P(A)
\end{aligned}
\end{equation}
$$

## WLLN

> For any $\delta \ge 0$

$$
\begin{equation}
\begin{aligned}
P(|\widehat{X_n} - \mu| \ge \delta ) \le \frac{\sigma ^2}{\delta^2}  \frac{1}{n} 
\end{aligned}
\end{equation}
$$

## Central Limit Theorem

> Any Distribution with large samples is normal distribution

$$
\begin{equation}
\begin{aligned}
P(\widehat{X}  \le \alpha ) &= \Phi (\frac{\alpha - \mu}{\sigma / \sqrt{n}} )
\end{aligned}
\end{equation}
$$

# Parameter Estimation

## Mean Estimation

> Bias to esimate the performance of a estimator

$$
\begin{equation}
\begin{aligned}
Bias(\widehat{\Theta } ) &= E(\widehat{\Theta } - \theta ) = E(\widehat{\Theta }) - \theta  \\
MSE(\Theta ) &= E(\widehat{\Theta } - \theta )^2 \\
&= E^2(\widehat{\Theta } - \theta ) + V(\widehat{\Theta } - \theta ) \\
&= Bias^2(\widehat{\Theta } ) + V(\widehat{\Theta } ) \\
&= \frac{\sigma ^2}{n} \ \text{(Unbiased)} 
\end{aligned}
\end{equation}
$$

- Bias is classified into **positive, negative and unbiased** based on this value

## Variance Estimation, Bessel Correction

> Raw Sample Variance. Take $n$ sample from each independent experiment(a total of $r$ experiments)

$$
\begin{equation}
\begin{aligned}
E(RSV) &= \frac{n-1}{n} \sigma^2 \\
\therefore \frac{n-1}{n}  S^2 &= \frac{1}{n}  \sum_{i=1}^{n} (X_i - \mu)^2 \\
S^2 &= \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \mu)^2 \ \text{Bessel Correction} 
\end{aligned}
\end{equation}
$$

$S^2$ is called sample variance

## Predict Normal Outcome

$$
\begin{equation}
\begin{aligned}
p &= P(-z_p \le Z \le z_p) \\
p &= 2 \Phi(z_p) - 1 \\
z_p &= \Phi^{-1} (\frac{1+p}{2} )
\end{aligned}
\end{equation}
$$

- Therefore, the smallest interval with prob $\ge p$ is $(\mu -z_p \sigma ,\mu + z_p \sigma)$

## Confidence Interval

$$
\begin{equation}
\begin{aligned}
(\overline{X} - z_p \frac{\sigma }{\sqrt{n}}, \overline{X} + z_p \frac{\sigma }{\sqrt{n}} )
\end{aligned}
\end{equation}
$$
