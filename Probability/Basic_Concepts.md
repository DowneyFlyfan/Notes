---
id: Basic_Concepts
aliases: []
tags: []
---

# Don't Know

1. Probability in the Space

$$
\begin{equation}
\begin{aligned}
P(E) &= \frac{|E|}{|\Omega| } 
\end{aligned}
\end{equation}
$$

2. Conditional Probability & General Probability

$$
\begin{equation}
\begin{aligned}
P(F | E) &\stackrel{?}{=} P(F)
\end{aligned}
\end{equation}
$$

3. 概率空间分类

| Category | Description |
|---|---|
| Multiple Events | General Space |
| Equiprobable Space | Uniform Space |

$$
\begin{equation}
\begin{aligned}
E \perp \! \! \! \perp F
\end{aligned}
\end{equation}
$$

4. Total Probability & Bayes Rules

$$
\begin{equation}
\begin{aligned}
P(A) &= \sum_{i=1}^{n} P(A | E_i) P(E_i)
\end{aligned}
\end{equation}
$$

$$
\begin{equation}
\begin{aligned}
P(A|B) &= \frac{P(B|A)P(A)}{P(B)}
\end{aligned}
\end{equation}
$$

Alternatively, using the law of total probability, if $E_1, E_2, \dots, E_n$ are a partition of the sample space $\Omega$ and $P(E_i) > 0$ for all $i$, then for any event $A$ such that $P(A) > 0$:

$$
\begin{equation}
\begin{aligned}
P(E_i|A) &= \frac{P(A|E_i)P(E_i)}{\sum_{j=1}^{n} P(A|E_j)P(E_j)}
\end{aligned}
\end{equation}
$$
