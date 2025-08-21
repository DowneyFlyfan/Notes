---
id: LR-Schedule
aliases: []
tags:
  - AI
---

| 调度器             | 公式                                                                                                | 实现代码                                                                   |
| :----------------- | :-------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------- |
| Cosine Annealing LR | $\eta = \eta_{min} + \frac{1}{2} (\eta_{max} - \eta_{min}) \lbrack 1 + \cos ( \frac{t}{T_{max}} \pi) \rbrack$ | `scheduler = lr_scheduler.CosineAnnealingLR(optimizer, T_max=100)`       |
| Exponential LR     | $lr = lr \times \gamma^t$                                                                           | `lr_scheduler = torch.optim.lr_scheduler.ExponentialLR(optimizer=optimizer, gamma=args.gamma)` |
