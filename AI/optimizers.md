---
id: optimizers
aliases: []
tags: []
---

| Optimizer | Update Formula | Key Parameters |
|---|---|---|
| **SGD** (Stochastic Gradient Descent) | $v_t = \gamma v_{t-1} + \eta \nabla_{\theta} J(\theta)$ <br> $\theta_t = \theta_{t-1} - v_t$ | $v$ (动量), $\gamma$ (动量参数，一般接近1), $\eta$ (学习率), $J(\theta)$ (损失函数) |
| **Adam** (Adaptive Momentum Estimation) | $g_t = \nabla_{\theta} J(\theta_t)$ <br> $m_t = \beta_1 m_{t-1} + (1 - \beta_1) g_t$ <br> $v_t = \beta_2 v_{t-1} + (1 - \beta_2) g_t^2$ <br> $\hat{m}_t = m_t / (1 - \beta_1^t)$ <br> $\hat{v}_t = v_t / (1 - \beta_2^t)$ <br> $\theta_t = \theta_{t-1} - \eta \cdot \hat{m}_t / (\sqrt{\hat{v}_t} + \epsilon)$ | $\eta$ (学习率), $\beta_1$ (一阶矩衰减率), $\beta_2$ (二阶矩衰减率), $\epsilon$ (平滑项，防止除零) |
