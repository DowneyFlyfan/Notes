---
id: Transmission
aliases: []
tags:
  - Math
---

# Introduction

## Channel Model

![](./imgs/Transimission/Channel_Model.png)

# Flip Channel

## Binary Symmetric Channel

![](./imgs/Transimission/Binary_Symmetric_Channel.png)

### Input, Output and Noise

> $p$ is the prob of noise occurence

$$
\begin{equation}
\begin{aligned}
Y &= (X+Z) \mod 2 \\
P(X) &= \begin{cases}
\alpha & x =0 \\
1 - \alpha & x = 1
\end{cases} \\
P(Z) &= \begin{cases}
p & z = 1 \\
1 -p & z = 0 
\end{cases} \\
P(Y = 0 | X = 0) &= 1 - p \\
P(Y = 1 | X = 1) &= 1 - p \\
\end{aligned}
\end{equation}
$$

### Prob of Right Outcome

> Model to determine the input using postrior prob

$$
\begin{equation}
\begin{aligned}
P(X=0|Y=b) &= \frac{P(Y=b|X=0) P(X=0)}{P(Y=b)} \\
P(X=1|Y=b) &= \frac{P(Y=b|X=1) P(X=1)}{P(Y=b)} \\
\widehat{X}  &= \begin{cases}
0 &  P(X=0|Y=b) > P(X=1|Y=b) \\
1 &  P(X=0|Y=b) < P(X=1|Y=b)
\end{cases} \\
\therefore L(b) &= \frac{P(Y=b | X = 0)}{P(Y=b | X =1)}  \overset{\hat{X}=0}{\underset{\hat{X}=1}{\gtreqqless}} \frac{\alpha }{1 - \alpha } \\
\end{aligned}
\end{equation}
$$

> Likelihood Ratio

$$
\begin{equation}
\begin{aligned}
L(1) &= \frac{p}{1-p} \\
L(0) &= \frac{1-p}{p}
\end{aligned}
\end{equation}
$$

### Improve Accuracy - Encoding

> Simpliest Encoding - Repetition Encoding

$X_i, i \in [1,n]$ are i.i.d random variables, sent same bit $n$ times

> New Log Likelihood

$$
\begin{equation}
\begin{aligned}
U &= \sum_{i=1}^{n} \mathbb{I} (b_i=0), V = \sum_{i=1}^{n} \mathbb{I} (b_i=1) \\
L(b) &= \frac{P(Y_1 =b_1 | X =0) P(Y_2=b_2 | X = 0) ... }{P(Y_1 =b_1 | X =1) P(Y_2=b_2 | X = 1) ... } \\
\sum_{i=1}^{n} LLR(b_i) &= \sum_{i=1}^{n} \log L(b_i) \\
&= U \log(\frac{p}{1-p} ) - V\log(\frac{p}{1-p} )  \\
&
\overset{\hat{X}=0}{\underset{\hat{X}=1}{\gtreqqless}} \frac{\alpha }{1 - \alpha } \\
U &\overset{\hat{X}=0}{\underset{\hat{X}=1}{\gtreqqless}}V, \alpha  = \frac{1}{2}  
\end{aligned}
\end{equation}
- [ ] $$

### Evaluation (To be Continued)
