---
id: VAE
aliases: []
tags:
  - AI
---



1. Process
    
- ![](paste-87cb2ee57e4cd0b1c095bdc2f75a567554e94682.jpg)  


$$
\begin{equation}
\begin{aligned}
p(Z) &= \sum_X p(Z|X)p(X) = \sum_X \mathcal{N}(0, I)p(X) = \mathcal{N}(0, I) \sum_X p(X) = \mathcal{N}(0, I) \\ 
Loss &= ||\hat X - X||_2^2 + D_{KL} \big(\mathcal N(\mu, \sigma^2) | \mathcal N(0, I)\big) \\ 
&= ||\hat X - X||_2^2 + \frac{1}{2} (-\log \sigma^2 + \mu^2 + \sigma^2 -1) \\ 
&= Reconstruction \ Loss + KL \ Loss \\ Z 
&= \mu + \sigma \epsilon, \epsilon \sim \mathcal N(0, \pmb I)
\end{aligned}
\end{equation}
$$

2. Insights

- **采样不可导，采样结果可导**
    
*   VAE 的 Bayes 理解

- ![](paste-9ab398d73fa721484f04538863f500c37f9cd752.jpg)

- ![](paste-760fa664a340cbc4f85fe742c1291bd439182fc7.jpg)  

- ![](paste-276ccc31674c8065fbcf77692fb5f351e172a213.jpg)

- ![](paste-306bd14ca14ec11ce83ab4209caba5349714c349.jpg)  

- ![](paste-b52b5edd2daa3f299cbf0155c192eb3c11f6927e.jpg)

- 只采一个$Z$

![](paste-41030db23aa5d58ecb0bd3f00a9753dcd5cb274f.jpg)  
      
- 所以 重构损失 + KL 损失 可以由第一个式子中的 KL 损失表示
