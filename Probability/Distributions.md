---
id: Distributions
aliases: []
tags: []
---

# Important Distributions and Their Properties

## Table

| Distribution Name | Type | Parameters | Formula | Expectation | Variance | Notes |
|---|---|---|---|---|---|---|
| Uniform | Continuous | $a, b$ | $f(x) = \dfrac{1}{b-a}$ for $a \le x \le b$, and $0$ otherwise | $\dfrac{a+b}{2}$ | $\dfrac{(b-a)^2}{12}$ | |
| Geometric | Discrete | $p$ | $P(X=k) = (1-p)^{k-1}p$ for $k \in \{1, 2, 3, \dots\}$ | $\dfrac{1}{p}$ | $\dfrac{1-p}{p^2}$ | Memoryless property |
| Hypergeometric | Discrete | $N, K, n$ | $P(X=k) = \dfrac{\binom{K}{k} \binom{N-K}{n-k}}{\binom{N}{n}}$ | $n\dfrac{K}{N}$ | $n\dfrac{K}{N}\dfrac{N-K}{N}\dfrac{N-n}{N-1}$ | Sampling without replacement |
| Bernoulli $B_n$ | Discrete | $p$ | $P(X=k) = p^k (1-p)^{1-k}$ for $k \in \{0, 1\}$ | $p$ | $p(1-p)$ | |
| Binomial $b_{p,n}(k)$ | Discrete | $n, p$ | $P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$ for $k \in \{0, 1, \dots, n\}$ | $np$ | $np(1-p)$ | Mode $\widehat{k} = \arg \max b_{p,n}(k)$ |
| Poisson | Discrete | $\lambda$ | $P(X=k) = \dfrac{e^{-\lambda} \lambda^k}{k!}$ for $k \in \{0, 1, 2, \dots\}$ | $\lambda$ | $\lambda$ | $F(x) = P(X \le x) = 1 - p^n$ |
| Exponential | Continuous | $\lambda$ | $f(x) = \lambda e^{-\lambda x}$ for $x \ge 0$, and $0$ otherwise | $\dfrac{1}{\lambda}$ | $\dfrac{1}{\lambda^2}$ | |
| Normal (Gaussian) | Continuous | $\mu, \sigma^2$ | $f(x) = \dfrac{1}{\sqrt{2\pi\sigma^2}} e^{-\dfrac{(x-\mu)^2}{2\sigma^2}}$ | $\mu$ | $\sigma^2$ | |

## Poisson Distribution

> The Poisson distribution is a discrete probability distribution that expresses the probability of a given number of events occurring in a fixed interval of time or space. These events must occur at a known constant mean rate and independently of the time since the last event.

- It starts with Binomial Distribution with a **constant mean**, with $n \xrightarrow{} \infty, p \xrightarrow{} 0, \lambda = np$

$$
\begin{equation}
\begin{aligned}
P(X = k) &= C_n^k p^k (1-p)^{n-k} \\
&= \underset{n \xrightarrow{} \infty }{lim}  \frac{n(n-1)...(n-k+1)}{k!}  \frac{\lambda^k}{n^k} (1 - \frac{\lambda}{n} )^n ( 1 - \frac{\lambda }{n})^{-k} \\
&= \frac{\lambda^k}{k!}  e^{-\lambda}
\end{aligned}
\end{equation}
$$

## Geometric Distribution

- 两人先后掷骰子，第一个掷出某个面的人赢. 不管骰子有多少面, 先手胜率都更大(奇数多一次)

$$
\begin{equation}
\begin{aligned}
P(odd) &= \sum_{i=1}^{\infty} P(X = 2i-1) \\
&= p (1 + q^2 +...) \\ 
&= \frac{1}{2-p} \gt p
\end{aligned}
\end{equation}
$$

- It is Memoryless

# Memoryless

1. Definition & Property

$$
\begin{equation}
\begin{aligned}
P(X = m + n | X > n) &= P(X = m) \\
E(X | X > n) &= \sum_{i=n+1}^{\infty } i P(X = i | X > n) \\
&= \sum_{j=1}^{\infty } (j+n) P(X=j) \\
&= n + E(X)
\end{aligned}
\end{equation}
$$

2. $3 \sigma$ for Gaussian Distribution: 68.27%, 95.45%, 99.73%

# Exponential

# Normal

$$
\begin{equation}
\begin{aligned}
\text{Continuous Correction Factor} CCF = \frac{\Delta x}{2} 
\end{aligned}
\end{equation}
$$

- $Delta x$ 是离散变量的最小间隔
