---
id: LLM-Indications-Methods
aliases: []
tags:
  - AI
---

# 指标

| 指标 | 描述/公式 |
|---|---|
| POPE (Prompt-Oriented Programming Evaluation) | 包括 Accuracy, Precision, Yes (50%最好), F1 Score |
| NLL (Negative Log-Likelihood) | 越小越好 <br> $NLL = - \sum_i \log x_i$ |
| Recall | $Recall = \frac{TP}{TP + FN}$ |

# 方法
| 方法 | 描述 |
|---|---|
| **LoRA (Low-Rank Adaptation)** | $W_{out} \in \mathcal R^{d_{1} \times d_{2}} = W_{in} \in \mathcal R^{d_{1} \times d_2} + A \in \mathcal R^{d_1 \times r} \times B \in \mathcal R^{r \times d_2}$ <br> 其中 $A$ 和 $B$ 是两个低秩矩阵, 这样在模型微调时可以**大幅减少参数量和计算量** |
| **LoRA 的改进** | 可以只更新 $A$ 而不更新 $B$, 收敛更快，效果更好 <br> 在参数初始化上下功夫 <br> 用SVD分解 $A, B$ |
