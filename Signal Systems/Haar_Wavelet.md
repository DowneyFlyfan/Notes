---
id: Haar_Wavelet
aliases: []
tags: []
---

# Haar Wavelet
*   Definition of Haar Function  
    ![](paste-18e5bc6fb5f86adb3f8cbae9f39607b64bf7831d.jpg)  
    **Haar Function**  
    (\begin{aligned} \psi(x) &= \begin{cases} 1 & 0 \le t \lt \frac{1}{2} \\ -1 & \frac{1}{2} \le t \lt 1 \\ 0 & otherwise \end{cases} \\ \varphi(x)&= \begin{cases} 1 & 0 \le t \le 1 \\ 0 & otherwise \end{cases} \end{aligned}$， 其中, (\psi(x)$为 Haar Function, (\varphi(x)$为Scale Function  
      
    **Haar Function for a pair  
    **(\psi_{n,k}(x) = 2^{n/2} \phi(2^n x - k)$  
    
*   Properties of Haar Function  
    **Orthogonality:**(\int \psi_{n_1, k_1}(x) \psi_{n_2, k_2}(x) dx = 0, n_2 \neq n_1 \ or \ k_2 \neq k_1$  
    **MRA (Multi-Resolution Analysis)  
    Compact**  
      
*   Definition & Property of Haar Matrix  
    ![](paste-325daa99f04ad97f9b4e43f5f9e01541bba7bd44.jpg)![](paste-21c14d114f0802466b232f257906bf44aec2ba31.jpg)![](paste-219c8e5b30ba62c40f16dad2b163a3cb1a116e0e.jpg) ((\otimes$表示Kronecker Product)  
      
    **Orthogonality & Symmetry:** (H_N^T H_N = I, H_N^T = H_N$  
    **Sparsity**
