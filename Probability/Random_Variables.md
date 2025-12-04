---
id: Random_Variables
aliases: []
tags:
  - Math
---

#  Probability Space

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

## Conditionals

$$
\begin{equation}
\begin{aligned}
P(F|E) &= \frac{P(EF)}{P(E)} , P(E) \neq 0
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

### Definition 

> Law of the Unconcious Statistians: Getting $E(Y)$ directly using $E(X)$

### Examples

1. Taking 2 balls from (2 RED, 3 BLUE) with / without replacement

- **Expectations are the same**, because 2 selected positions are **symmetric**

2. Take 2 numbers w/wo replacement from $1,3,6$ and from a **2-digit number** 

- **Expectations are the same**, it can also be explained by the **Linearity of Expectations** $R = 10X + Y \xRightarrow{} E(R) = 10 E(X) + E(Y) = 40.33$

3. **Runs**: For $n$ bits run. Each bit obeys $B_p$.

- 1st number is a run. Different bit from previous $p(1-p) + (1-p)p$ is a run

- Add them, you get $E(R) = 1 + 2(n-1) p(1-p)$

## Indicator Methods

> Core: The Linearity of Expectation goes beyond its independence.

$$
\begin{equation}
\begin{aligned}
I_i &= \begin{cases}
1 & \text{A Occurs}   \\
0 & \text{A doesn't occur} 
\end{cases} \\
E(X) &= E(\sum_{i}^{} I_i)
\end{aligned}
\end{equation}
$$

# Properties of Random Variables

## Expectation

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
E(\sum_{i}^{} a_i X_i + b ) &= \sum_{i}^{} a_i E(X_i) + b
\end{aligned}
\end{equation}
$$

1. 3 cards are randomly inserted in a circle made of a deck

- The expected number of cards between them are ?

$$
\begin{equation}
\begin{aligned}
E(L_1 + L_2 + L_3) &= 52 \\
E(L_1) &= E(L_2) = E(L_3) = \frac{52}{3}
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

## Independence & Correlation

1. Independence

$$
\begin{equation}
\begin{aligned}
P(X \cap Y) &= P(X) P(Y)
\end{aligned}
\end{equation}
$$


$$
\begin{equation}
\begin{aligned}
E(XY) &= E(X) E(Y) \\
V(X+Y) &= V(X) + V(Y)
\end{aligned}
\end{equation}
$$

2. Independence and Correlation

- $X \perp \! \! \! \perp Y \implies Cov(X,Y) = 0$, but $Cov(X,Y) = 0 \not\implies X \perp \! \! \! \perp Y$

## Variance & Standard Deviation & Covariance & Correlation Coefficient

| Concept | Definition(s) | Properties |
|---|---|---|
| **Variance** | $V(X) = \sum_{i}^{} \big[ x_i - E(x_i) \big]^2$ $V(X) = E(X^2) - E^2(X)$ | $V(aX +b) = a^2 V(X)$, $V(X + Y) = V(X) + V(Y) + 2Cov(X,Y)$ |
| **Standard Deviation** | $\sigma_x = \sqrt{V(X)}$ | $\sigma(aX+b) = \|a\| \sigma_x$ |
| **Covariance** | $Cov(X,Y) = E[ (X - E(X)) (Y - E(Y)) ]$ $Cov(X,Y) = E(XY) - E(X) E(Y)$ | $Cov(X, Y + Z) = Cov(X, Y) + Cov(X, Z)$  |
| **Covariance Matrix** | $\sum = \begin{pmatrix} Var(X) & Cov(X,Y) \\ Cov(Y, X) & Var(Y) \end{pmatrix}$ | - |
| **Correlation Coefficient** | $\rho_{X,Y} = \dfrac{Cov(X,Y)}{\sigma_X \sigma_Y}$ | $\rho(aX+b,cY+d) = sign(ac) \rho_{X,Y}$ |


