# Positional Encodings
*   CV

1.  Fourier Encoding (FE)  
    对于每一组输入坐标(\pmb v$的编码 (\gamma(v) = \[ a_1 \sin(2\pi b_1^T \pmb v), a_1 \cos(2\pi b_1^T \pmb v), ... , a_L^2\sin(2\pi b_L^T \pmb v), a_L^2 \cos(2\pi b_L^T \pmb v )], L = Length \ of \ encodings$  
    **  
    FE具有平移不变性, 能表示相对位置  
    **(\gamma(v_i) \cdot \gamma(v_j) = \sum_{m = 1}^L a_m^2 cos\[2\pi b_m^T (\pmb v_i - \pmb v_j)]$  
      
    
2.  Hash Encodings  
    在**较为密集的网格中，字典不够用** ，用hash编码弥补这一点  
    给定( primes = \[1, 2654435761, 805459861]$,对于输入的(2D/3D$坐标，零初始化一个(index$  
    然后进行(index \otimes x\[..., i] \* primes\[i]$  
    index用来取最近的整数坐标dictionary((num_{dims} , num_{encodings})$中的值, 同时**更新字典**  
      
    
3.  Densegrid Encodings  
    在**较为稀疏的网格中，字典够用**，就用dense-grid encoding  
    (\[x,y,z] \rightarrow index = x + y \times W + z \times HW$, 保证每一个坐标对应单一的index  
    index用来取最近的整数坐标dictionary((num_{dims} , num_{encodings})$中的值, 同时**更新字典**  
      
    
4.  Multi-Resolution Encodings  
    (\begin{aligned} b &= \exp\left(\frac{\ln(R_{max} / R_{min})}{L-1}\right) = \left( \frac{R_{max}}{R_{min}} \right)^{\frac{1}{L-1}} \\ R_l &= \lfloor R_{min} \cdot b^l \rfloor \\ \end{aligned}$  
      
    把这些resolution下的网格依次**根据dense与否**放入上面两个Encoding中,  
    输入**相机中采样的得到的三维空间点**, 使用**双线性插值**来计算需要的token

*   NLP  
    

1.  原版 QK-RoPE (Rotational Positional Encoding)\\[\begin{aligned} RoPE(x_m^{(1)}, x_m^{(2)}, m) &= \begin{bmatrix} \cos(m\theta) & -\sin(m\theta) \\ \sin(m\theta) & \cos(m\theta) \end{bmatrix} \begin{bmatrix} x_m^{(1)} \\ x_m^{(2)} \end{bmatrix} = \begin{bmatrix} x_m^{(1)}\cos(m\theta) - x_m^{(2)}\sin(m\theta) \\ x_m^{(2)}\cos(m\theta) + x_m^{(1)}\sin(m\theta) \end{bmatrix} \\ \Theta = \theta_i &= 10,000^{-\frac{2(i-1)}{d}} , where ( i \in \[1, 2, ..., 2d] ) \text{ for the 2d pairs of features} \\ \mathrm{RoPE}(x, m) &= xe^{mi\theta} \\ \langle \mathrm{RoPE}(q_j, m), \mathrm{RoPE}(k_j, n)\rangle &= \langle q_j e^{mi\theta}, k_j e^{ni\theta} \rangle \\ &= q_j k_j e^{mi\theta} \overline{e^{ni\theta}} \\ &= q_j k_j e^{(m - n)i\theta} \\ &= \mathrm{RoPE}(q_j k_j, m - n) \end{aligned}]  
    
2.  从QK-RoPE 到 VO-RoPE  
    \\[\begin{aligned} QK-RoPE:& s_{i,j} = (\boldsymbol{\mathcal{R}}_i\boldsymbol{q}_i)^{\top} (\boldsymbol{\mathcal{R}}_j\boldsymbol{k}_j) = \boldsymbol{q}_i^{\top}\boldsymbol{\mathcal{R}}_i^{\top}\boldsymbol{\mathcal{R}}_j\boldsymbol{k}_j=\boldsymbol{q}_i^{\top}\boldsymbol{\mathcal{R}}_{j-i}\boldsymbol{k}_j \\ a_{ij} &= softmax(s_{ij}) \\ o_{ij} &= \sum_j a_{i,j}\boldsymbol{v}_j \\ VO-RoPE:& \boldsymbol{o}_i = \boldsymbol{\mathcal{R}}_i^{\top}\left(\sum_j a_{i,j} \boldsymbol{\mathcal{R}}_j\boldsymbol{v}_j\right)=\sum_j a_{i,j} \boldsymbol{\mathcal{R}}_i^{\top}\boldsymbol{\mathcal{R}}_j\boldsymbol{v}_j=\sum_j a_{i,j} \boldsymbol{\mathcal{R}}_{j-i}\boldsymbol{v}_j \end{aligned}]  
    

*   Insights

1.  适用性  
    (\mathrm{RoPE}$经常用于序列任务 (**没有可学习参数**)  
    Fourier Encoding作为一种无法学习，但具有平移不变性的编码，经常用于各类视觉任务  
    Hash / Densegrid / Multi-Resolution Encoding 适用于**多视角还原3D图**, **zero-shot(单图过拟合)** 等任务
