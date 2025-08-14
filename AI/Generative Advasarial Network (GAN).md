# Generative Advasarial Network (GAN)
*   R3GAN  
    

1.  训练策略  
    生成器(G)和辨别器(D)交替训练  
      
    
2.  损失函数  
    有梯度惩罚 和 生成器与辨别器 之间的差异\\[\begin{aligned} L_{\text{RpGAN}}(\theta, \psi) &= \mathbb{E}_{\substack{\mathbf{z} \sim p_z \\ \mathbf{x} \sim p_D}} \[f(D_\psi(G_\theta(\mathbf{z})) - D_\psi(\mathbf{x}))] \\ R_1(\psi) &= \frac{\gamma}{2}\mathbb{E}_{\mathbf{x} \sim p_D} \[\|\nabla_{\mathbf{x}} D_\psi(\mathbf{x})\|_2^2] \\ R_2(\theta, \psi) &= \frac{\gamma}{2}\mathbb{E}_{\mathbf{x}' \sim p_G} \[\|\nabla_{\mathbf{x}'} D_\psi(\mathbf{x}')\|_2^2] \\ \mathcal{L}_D^{\text{R3GAN}} &= -L_{\text{RpGAN}}(\theta, \psi) + R_1(\psi) + R_2(\theta, \psi) \\ \end{aligned}]
