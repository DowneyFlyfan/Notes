---
id: VAR
aliases: []
tags:
  - AI
---

# 基本结构 + 训练策略

## Train

### VQVAE-2

1. encoder是经典的多层下采样 + Conv + Attn, decoder是多层临近上采样 + Conv + Attn

### Quantization

- 将encoder的输出(逐层递减latent images)进行area分别下采样至多个patch $(b,c,h_i, w_i)$, $h_i \in (1, h_e), w_i \in (1, w_e)$

- 计算输出和codebook中各个token的欧式距离，或归一化后相乘计算夹角，
取乘积最大或距离最小的token $(b,c,h_i, w_i)$, $h_i \in (1, h_e), w_i \in (1,w_e)$

- 对token进行bicubic上采样至tokens $(b,c,h_e,w_e)$, 再放入shared Conv(比如16个patch共用8个Conv，更高效，index按距离排序)

- 输出latent images $(b,c,h_e, w_e)$，累加作为decoder输出

- Loss当然是按VQVAE的经典做法，一条路更新codebook, 一条路更新VAE

### VAR

- 将VQVAE encoder输出的latent images $(b,c,h_e, w_e)$ 做个拼接$(token, pos_emb, lvl_emb)$, 然后取token index
输出的token index拼一起 $(b,l)$ 作为GT

- 对每一层的累加和(即中间的累加和)进行area下采样至next scale $(b,l_i,c)$
- 把 next scale 拼起来得到var inp $(b,l_{total}, c)$

- 将输入label作为condition和零初始化的另一半condition混合，作为Ada-ln zero的输入,把输入放入 **Ada-LN zero Causal Attention**, 得到输出**logits**
- 将logits和gt做交叉熵损失

## 推理策略

- 没有causal mask, 多了kv cache

- 直接从logits中采样放入VAE decoder进行image regeration

# Insights

- VQVAE-2作为image generator可能不够好，但训练出来的encoder和codebook作为特征提取器是非常好的
