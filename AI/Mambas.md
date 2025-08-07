---
id: Mambas
aliases: []
tags: []
---


# Mamba及其变体
1.  原版Mamba结构  
    ![](paste-ee8b3b2b13207b7d719bea29b7fe3dde85c1f9d8.jpg)  
    **Mamba Block**  
    (b$: batch size, (l$: sequence length (patch number in CV), (d$: Model Dimension (channels for CV), (e$: expansion factor, (dt$:hidden dim of delta, (n$: Hidden dim  
    (x(b, l, d) \rightarrow \[Linear] \rightarrow x(b, l, de), res(b, l, de)$  
    (res(b,l,de) \rightarrow \[SiLu] \rightarrow res(b, l, de)$  
    (x(b, l, de) \rightarrow \[Conv1d] \rightarrow x(b,l, de) \rightarrow \[SiLu] \rightarrow x(b, l, de) \rightarrow \[SSM] \rightarrow y -> \[y = y\*res] \rightarrow y (b, l, de)$  
      
    **SSM Block**  
    (x \rightarrow \[Linear] \rightarrow \Delta (b, l, dt), B(b,l,n), C(b,l,n)$  
    (\Delta (b, l,dt) \rightarrow \[Linear] \rightarrow \Delta(b, l, de) $  
    (A(de, n), D(de,): one-init$  
    (Selective Scan (\Delta, x, A, B, C, D) \rightarrow y$  
      
    **Selective Scan (最消耗算力的地方，以下是一种实现方式, 官方有高效的GPU实现）**  
    把上面的(x$改成(u$, (x$另外初始化  
    (\Delta A = e^{\Delta A}: (b,l,de)\*(de,n) \rightarrow (b,l,de,n)$  
    (\Delta B = \Delta B u: (b,l,de) \* (b,l,n)\*(b,l,de) \rightarrow (b,l,de,n)$  
    (\begin{aligned} for i = 0:l:& \\ x(b,de,n) &= x(b,de,n) \times \Delta A\[:,i] (b, de, n) + \Delta B u\[:,i] (b,de, n) \\ y_i &= x \times C (b, de) \end{aligned}$  
    然后把所有(y$拼起来再(y = y + Du$，得到(y(b,l,de)$
