---
id: Distributions
aliases: []
tags:
  - Math
---

# Important Distributions

## Table

| Distribution Name | Type | Parameters | Formula | Expectation | Variance | Notes |
|---|---|---|---|---|---|---|
| Uniform | Continuous | $a, b$ | $f(x) = \dfrac{1}{b-a}$ for $a \le x \le b$, and $0$ otherwise | $\dfrac{a+b}{2}$ | $\dfrac{(b-a)^2}{12}$ | |
| Bernoulli $B_n$ | Discrete | $p$ | $P(X=k) = p^k (1-p)^{1-k}$ for $k \in \{0, 1\}$ | $p$ | $p(1-p)$ | |
| Binomial $b_{p,n}(k)$ | Discrete | $n, p$ | $P(X=k) = \binom{n}{k} p^k (1-p)^{n-k}$ for $k \in \{0, 1, \dots, n\}$ | $np$ | $np(1-p)$ | Mode $\widehat{k} = \arg \max b_{p,n}(k)$ |
| Geometric | Discrete | $p$ | $P(X=k) = (1-p)^{k-1}p$ for $k \in \{1, 2, 3, \dots\}$ | $\dfrac{1}{p}$ | $\dfrac{1-p}{p^2}$ | Memoryless property |
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

### Examples

- Roll a Die

> Two people take turns rolling a die; the first to roll a specific face wins. Regardless of the number of faces, the first player has a higher win rate.

$$
\begin{equation}
\begin{aligned}
P(odd) &= \sum_{i=1}^{\infty} P(X = 2i-1) \\
&= p (1 + q^2 +...) \\ 
&= \frac{1}{2-p} \gt \frac{1}{2} 
\end{aligned}
\end{equation}
$$

- NASA Mishap

> $p$ is the mishap probability for each launch. After 10 launches, what is the probability of a mishap

$$
\begin{equation}
\begin{aligned}
P(x=n) &= p(1-p)^{n-1} \\
\frac{dP}{dp} &= (1-p)^{n-1} + p(n-1)(1-p)^{n-2} \\
&= (1-np) (1-p)^{n-2} \\
\therefore p &= \frac{1}{n}  \\
\therefore \max(P(x=n)) &= \frac{(1 - 1/n)^n}{n-1} \lesssim \frac{1}{e(n-1)}
\end{aligned}
\end{equation}
$$

### Old & New Money

- Old Dad funds $n$ companies

$$
\begin{equation}
\begin{aligned}
X &\sim G_{0.2} \\
\therefore P(Success) &= P(X \le n) \\
&= 1 - (0.8)^n \\
E(X) &= 5
\end{aligned}
\end{equation}
$$

- New Dad funds **infinite** companies, keeps $2^X$ fraction of the company

$$
\begin{equation}
\begin{aligned}
X &\sim G_{0.2} \\
P(Success) &= \sum_{i=0}^{\infty} P_i = 1 \\
E(X) &= \sum_{i=0}^{\infty} r^i P(X=k) \\
&= \frac{rp}{1 - (1-p)r} 
\end{aligned}
\end{equation}
$$

## Exponential



## Normal

$$
\begin{equation}
\begin{aligned}
\text{Continuous Correction Factor } CCF = \frac{\Delta x}{2} 
\end{aligned}
\end{equation}
$$

- $\Delta x$ 是离散变量的最小间隔

- $3 \sigma$ for Gaussian Distribution: 68.27%, 95.45%, 99.73%

# Important Properties

## Memoryless

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

- Experiment Time has to be $\ge 1$

## Gaussian Integral

$$
\begin{equation}
\begin{aligned}
I &= \int_{0}^{\infty}  e^{-a x^2} dx \\
I^2 &= \iint_{0}^{\infty}  e^{-a (x^2 + y^2)} dx dy \\
&= \int_{0}^{2 \pi} \int_{0}^{\infty}  e^{-ar^2} r dr d \theta \\
&= 2 \pi \big[ - \frac{1}{2a} e^{-a r^2}  \big]_0^{\infty } \\
&= \frac{\pi}{a} \\
\therefore I &= \sqrt{\dfrac{\pi}{a} }
\end{aligned}
\end{equation}
$$
