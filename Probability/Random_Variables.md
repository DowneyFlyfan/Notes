---
id: Random_Variables
aliases: []
tags:
  - Math
---

# Probability Space

## Probability in the Space

1. Definition1 - Space

| Category | Description |
|---|---|
| Multiple Events | General Space |
| Equiprobable Space | Uniform Space |


$$
\begin{equation}
\begin{aligned}
P(E) &= \begin{cases}
\sum_{x \in \Omega }^{} p(x) & General \\
\dfrac{|E|}{|\Omega| } & Uniform
\end{cases}
\end{aligned}
\end{equation}
$$

2. Definition2 - map:

- For instance, $\mathcal{R} \xrightarrow{} [0,1]$

- For multiple events, $\mathcal{R} \times \mathcal{R} \xrightarrow{}  [0,1]$

## Conditionals & Independence

$$
\begin{equation}
\begin{aligned}
P(F|E) &= \frac{P(EF)}{P(E)} , P(E) \neq 0 \\
P(X) P(Y) &= P(XY) \xrightarrow{} X \perp \! \! \! \perp Y
\end{aligned}
\end{equation}
$$

- Conditional Probability is asymmetric


| Condition           | Implication         | Relationship       |
|---------------------|---------------------|--------------------|
| $P(F \| E) = P(F)$   | $E \perp \! \! \! \perp F$ | Independent        |
| $P(F \| E) > P(F)$   |                     | Positive Correlated |
| $P(F \| E) < P(F)$   |                     | Negative Correlated |

## Marginals

$$
\begin{equation}
\begin{aligned}
P(X = x) &= \sum_{y}^{} p(x,y) \\
P(Y = y) &= \sum_{x}^{} p(x,y)
\end{aligned}
\end{equation}
$$

## Total Probability & Bayes Rules

### Definitions

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

### Applications

$$
\begin{equation}
\begin{aligned}
P(E_i|A) &= \frac{P(A|E_i)P(E_i)}{\sum_{j=1}^{n} P(A|E_j)P(E_j)}
\end{aligned}
\end{equation}
$$

### Conditioanl Expectation

$$
\begin{equation}
\begin{aligned}
E(A) &= \sum_{i=1}^{n} E(A | E_i) P(E_i)
\end{aligned}
\end{equation}
$$

# Random Variables

## Distribution of Probabilities

$$
\begin{equation}
\begin{aligned}
P(Y = y) &= P(X = g^{-1}(Y))
\end{aligned}
\end{equation}
$$

- Constant $g$

$$
\begin{equation}
\begin{aligned}
P(Y = a) &= P(X = g^{-1}(a)) = P(X \in \Omega) = 1
\end{aligned}
\end{equation}
$$

## CDF, Right CDF, PDF, PMF

- interval , disjoint probabilities

## LOTUS

1. Definition 

- Law of the Unconcious Statistians: Getting $E(Y)$ directly using $E(X)$

2. Example

- Taking 2 balls from (2 RED, 3 BLUE) with / without replacement

- **Expectations are the same**

- When without replacement, 2 positions that you pick up the balls are **symmetric**

## Indicators

$$
\begin{equation}
\begin{aligned}
I_i &= \begin{cases}
1 & Events \ Occurred \\
0 & Otherwise
\end{cases} \\
E(X) &= E(\sum_{i}^{} I_i)
\end{aligned}
\end{equation}
$$

# Properties of Random Variables

## Min, Max, Median, Mode

$$
\begin{equation}
\begin{aligned}
x_{min} &= \min \lbrace x \in \Omega , p(x) \ge 0  \rbrace \\
x_{max} &= \max \lbrace x \in \Omega , p(x) \ge 0  \rbrace \\
P(x \ge x_{median}) &\ge \frac{1}{2}  \\
P(x \le x_{median}) &\ge \frac{1}{2}  \\
x_{mode} &= x: \big\{ \arg \max p(x) \big\}
\end{aligned}
\end{equation}
$$

## Expectations

### Definitions for General Space and Samples

$$
\begin{equation}
\begin{aligned}
E(X) &= \sum_{i}^{} p(x_i) x_i , Formula\\
&= \sum_{i}^{} \Big[ \frac{p(x_i) n}{n} \Big] x_i, Samples \\
&= \
HKsum_{i=1}^{\infty} P(X \ge i)
\end{aligned}
\end{equation}
$$

### Linearity

$$
\begin{equation}
\begin{aligned}
E(aX + b) &= aE(x) + b \\
E(X + Y) &= E(X) + E(Y)
\end{aligned}
\end{equation}
$$

### Independence

$$
\begin{equation}
\begin{aligned}
X \perp \! \! \! \perp Y \xLeftrightarrow{} E(X)E(Y) = E(XY)
\end{aligned}
\end{equation}
$$

## Variations, Standard Deviations

### Definitions

$$
\begin{equation}
\begin{aligned}
V(X) &= \sum_{i}^{} \big[ x_i - E(x_i) \big]^2 \\
&= E(X^2) - E^2(X) \\
\sigma_x &= \sqrt{V(X)}
\end{aligned}
\end{equation}
$$

### Properties

$$
\begin{equation}
\begin{aligned}
V(aX +b) &= a^2 V(X) \\
\sigma(aX+b) &= |a| \sigma_x \\
X \perp \! \! \! \perp Y &\xLeftrightarrow{} V(X + Y) = V(X) + V(Y) \\
\end{aligned}
\end{equation}
$$

## Covaraiance, Correlation Coefficient

### Definition

$$
\begin{equation}
\begin{aligned}
Cov(X,Y) &= E(XY) - E(X) E(Y) \\
\rho_{X,Y} &= \frac{Cov(X,Y)}{\sigma_X \sigma_Y} 
\end{aligned}
\end{equation}
$$

### Properties

$$
\begin{equation}
\begin{aligned}
Cov(X, Y + Z) &= Cov(X, Y) + Cov(X, Z) \\
V(X + Y) &= V(X) + V(Y) + 2Cov(X,Y) \\
\rho(aX+b,cY+d) &= sign(ac) \rho_{X,Y}
\end{aligned}
\end{equation}
$$
