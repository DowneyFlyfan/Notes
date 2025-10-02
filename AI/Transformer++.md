---
id: Transformer++
aliases: []
tags:
  - AI
---

# Original Transformer

$$
\begin{equation}
\begin{aligned}
Attention &= Softmax(\frac{Q\cdot K^T}{\sqrt{d}} V) \\ 
Q &= x W_Q, K = x W_K, V = x W_K \\
Input & \xrightarrow{}  Encoder*n \xrightarrow{}  Decoder*n  
\end{aligned}
\end{equation}
$$

Encoder = Multi-Head SA -> BN -> MLP -> Residual -> BN  
Decoder = Causal Attention -> Residual -> BN -> Encoder-Decoder Attention -> BN -> MLP -> BN  
Encoder - Decoder Attention = Encoder Output -> MHSA -> 把作为权重赋值到Encoder Output 作为下一步的输入  

# ViT  
    
1. 结构  

Patch Embedding + Positional Embedding + Class Token -> Transformer -> MLP ( Classification Head)  
分类: ViT-B(Base, dim = 768), ViT-S(Small, 368), ViT/8( 8\*8 的patch, 更多patch)  
      
2. Vision-Transformer Attention 结构拆解  

- $X_{image} \in R^{B \times C \times H \times W}$ 变成 $N = \frac{H}{P} \times \frac{W}{P}$个patch 

- $\rightarrow Patch Embed \rightarrow$ 展平成 $X \in R^{B \times N \times ( C \times P^2)} \rightarrow MLP -> X \in R^{B \times N \times D} \rightarrow MLP \rightarrow Q,K,V \in R^{B \times h \times N \times d_k}, d_k = \frac{D}{h} \rightarrow$  

- $attn = softmax( \frac{QK^T}{\sqrt{d_k}} ) \in R^{B \times h \times N \times N}$, 也就是每个patch **(注意,patch已经被压缩成d了)** 之间的相似度矩阵 (\rightarrow$

- $Y_k = attn \times V \in R^{B \times h \times N \times d_k} \rightarrow Y = cat(Y_k, dim = 1) \in R^{B \times N \times D}$  
