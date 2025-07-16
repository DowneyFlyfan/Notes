
1.  **Forward (Add Noise)**  
    (\begin{aligned} x_t &\sim \mathcal N(\sqrt{1 - \beta_t} x_{t-1}, \beta_t \pmb I) = \mathcal N(\sqrt\alpha_t, (1 - \alpha_t) \pmb I ) \\\ x_t &= \sqrt{1 - \beta_t} x_{t-1} + \sqrt{\beta_t} \epsilon; \epsilon \sim \mathcal N(0, I) \\\ &= \sqrt{1 - \beta_t} ( \sqrt{1 - \beta_{t-1}} x_{t-2} + \sqrt{\beta_{t-1}} \epsilon) + \sqrt{\beta_{t}} \epsilon \\\ &= ... \\\ &= \sqrt{\bar{\alpha_t}} x_0 + \sqrt{1 - \bar{\alpha_t}} \epsilon \\\ \alpha_t &= 1 - \beta_t \\\ \bar{\alpha_t} &= \sum_{i = 0}^T \alpha_t \\\ x_T &\sim N(0, I) \end{aligned}$  
      
    
2.  **Backward (Sample / Diffusion, Denoise)(\begin{aligned} q(x_{t-1}|x_t, x_0) &= q(x_t|x_{t-1}, x_0) \frac{q(x_{t-1}|x_0)}{q(x_t|x_0)} \\ &= \frac{1}{\sqrt{2\pi}\beta_t} e^{-\dfrac{(x_t - \sqrt{1-\beta_t}x_{t-1})^2}{2\beta_t}} \times \frac{1}{\sqrt{2\pi(1-\bar{\alpha}_{t-1})}} e^{-\dfrac{(x_{t-1} - \sqrt{\bar{\alpha}_{t-1}}x_0)^2}{2(1-\bar{\alpha}_{t-1})}} \quad \times \sqrt{2\pi(1-\bar{\alpha}_t)} e^{-\dfrac{(x_t - \sqrt{\bar{\alpha}_t}x_0)^2}{2(1-\bar{\alpha}_t)}} \\ &= \frac{1}{\sqrt{2\pi}\beta_t} e^{-\dfrac{(x - \mu)^2}{2\sigma^2}} \\ \sigma^2 &= \beta_t \frac{1 - \bar{\alpha}_{t-1}}{1 - \bar{\alpha}_t} \\ \mu &= \frac{\sqrt{\alpha_t}(1 - \bar{\alpha}_{t-1})}{1 - \bar{\alpha}_t} \mathbf{x}_t + \frac{\sqrt{\bar{\alpha}_{t-1}} \beta_t}{1 - \bar{\alpha}_t} \mathbf{x}_0 \\ &= \frac{1}{\sqrt{\alpha_t}} \left( x_t - \frac{1 - \alpha_t}{\sqrt{1 - \bar{\alpha}_t}} \epsilon_t \right) \\ &= \sqrt{\bar{\alpha}_{t-1}} \mathbf{x}_0 + \sqrt{1 - \bar{\alpha}_{t-1} - \tilde{\beta}_t} \cdot \frac{\mathbf{x}_t - \sqrt{\bar{\alpha}_t} \mathbf{x}_0}{\sqrt{1 - \bar{\alpha}_t}} \\ \tilde{\beta}_t(\eta) &= \eta \frac{(1 - \bar{\alpha}_{t-1})}{(1 - \bar{\alpha}_t)} \cdot \beta_t , \eta = 1: DDPM; \eta = 0: DDIM\\ \therefore q(x_{t-1}|x_t, x_0) &= \mathcal{N} \left(x_t; \frac{1}{\sqrt{\alpha_t}} \left( x_t - \frac{1 - \alpha_t}{\sqrt{1 - \bar{\alpha}_t}} \epsilon_t \right),\ \beta_t \frac{1 - \bar{\alpha}_{t-1}}{1 - \bar{\alpha}_t} \mathbf{I} \right) \\ &= \mathcal{N}\big(\mathbf{x}_{t-1}; \sqrt{\bar{\alpha}_{t-1}} \mathbf{x}_0 + \sqrt{1 - \bar{\alpha}_{t-1} - \tilde{\beta}_t} \cdot \frac{\mathbf{x}_t - \sqrt{\bar{\alpha}_t} \mathbf{x}_0}{\sqrt{1 - \bar{\alpha}_t}}, \tilde{\beta}_t \mathbf{I} \big) \end{aligned}$**

3.  **Loss Explanation  
    VLB(变分下界) 推导  
    **(\begin{aligned} \log p_\theta(\mathbf{x}_0) &= \log \int p_\theta(\mathbf{x}_{0:T}) \, d\mathbf{x}_{1:T} \\ &\geq \mathbb{E}_{q(\mathbf{x}_{1:T} \mid \mathbf{x}_0)} \left\[ \log \frac{p_\theta(\mathbf{x}_{0:T})}{q(\mathbf{x}_{1:T} \mid \mathbf{x}_0)} \right] \quad \text{(Jensen不等式)} \\ &= \mathbb{E}_q \Bigg\[ \log \frac{p_\theta(\mathbf{x}_T) \prod_{t=1}^T p_\theta(\mathbf{x}_{t-1} \mid \mathbf{x}_t)}{\prod_{t=1}^T q(\mathbf{x}_t \mid \mathbf{x}_{t-1})} \Bigg] \quad \text{(联合分布分解)} \\ &= \mathbb{E}_q \Bigg\[ \log p_\theta(\mathbf{x}_T) + \sum_{t=1}^T \log \frac{p_\theta(\mathbf{x}_{t-1} \mid \mathbf{x}_t)}{q(\mathbf{x}_t \mid \mathbf{x}_{t-1})} \Bigg] \quad \text{(对数乘积转求和)} \\ &= \mathbb{E}_q \Bigg\[ \log \frac{p_\theta(\mathbf{x}_T)}{q(\mathbf{x}_T \mid \mathbf{x}_0)} + \sum_{t=2}^T \log \frac{p_\theta(\mathbf{x}_{t-1} \mid \mathbf{x}_t)}{q(\mathbf{x}_{t-1} \mid \mathbf{x}_t, \mathbf{x}_0)} + \log p_\theta(\mathbf{x}_0 \mid \mathbf{x}_1) \Bigg] \quad \text{(贝叶斯后验展开)} \\ &= -\underbrace{D_{\text{KL}}(q(\mathbf{x}_T \mid \mathbf{x}_0) \| p_\theta(\mathbf{x}_T))}_{\text{先验匹配项}} - \sum_{t=2}^T \underbrace{D_{\text{KL}}(q(\mathbf{x}_{t-1} \mid \mathbf{x}_t, \mathbf{x}_0) \| p_\theta(\mathbf{x}_{t-1} \mid \mathbf{x}_t))}_{\text{反向过程匹配项}} + \underbrace{\mathbb{E}_q \[\log p_\theta(\mathbf{x}_0 \mid \mathbf{x}_1)]}_{\text{重建项}} \\ &\triangleq L_{\text{VLB}} \end{aligned}$  
      
    **第一项** 和 **方差** 不涉及网络，因此化简后可以得到如下结果, 去掉常数就是我们的loss  
    (\begin{aligned} L_{VLB} &= \mathbb{E}\left\[ D_{KL}(q(\mathbf{x}_T \mid \mathbf{x}_0) \| p_{\theta}(\mathbf{x}_T)) + \sum_{t=2}^T D_{KL}(q(\mathbf{x}_{t-1} \mid \mathbf{x}_t, \mathbf{x}_0) \| p_{\theta}(\mathbf{x}_{t-1} \mid \mathbf{x}_t)) - \log p_{\theta}(\mathbf{x}_0 \mid \mathbf{x}_1) \right] \\ D_{KL}(P \| Q)_{\mathcal N} &= \log \frac{\sigma_2}{\sigma_1} + \frac{\sigma_1^2 + (\mu_1 - \mu_2)^2}{2 \sigma_2^2} - \frac{1}{2} \\ 2nd \ Term: &\frac{(1 - \alpha_t)^2}{2 \alpha t (1 - \bar{\alpha_t}) \tilde{\beta}_t^2} \| \epsilon_t - \epsilon_{\theta}(\mathbf{x}_t, t) \|^2 \\ 3rd \ Term: &\frac{1 - \bar{\alpha}_1}{2 \tilde{\beta}_1^2 \alpha_1} \| \epsilon_1 - \epsilon_{\theta}(\mathbf{x}_1, 1) \|^2 \end{aligned}$  
      
    
4.  **Algorithm  
    **(\epsilon_{\theta}$**就是神经网络, 输入步数和图像，拟合标准正态分布  
    而**(\epsilon$**是一个符合正态分布的随机变量  
    ![](paste-b0e9572e36ac8cfcb4a3763ba96e7b3ab2f83ed8.jpg)![](paste-f69dcc6b1c464006d1da2931f6ecff16f2ecbff4.jpg)  
    Time Step Embeddings:**  
    (\begin{aligned} \text{timestep_embedding}(t, \text{dim}, \text{max_period}) &= \begin{cases} \left\[ \cos(\text{args}), \sin(\text{args}) \right], & \text{if } \text{dim} \text{ is even} \\ \left\[ \cos(\text{args}), \sin(\text{args}), 0 \right], & \text{if } \text{dim} \text{ is odd} \end{cases} \\ \text{half} &= \text{dim} // 2 \\ \text{freqs} &= \exp\left( -\ln(\text{max_period}) \cdot \frac{\text{torch.arange}(0, \text{half})}{\text{half}} \right) \\ \text{args} &= t \cdot \text{freqs} \end{aligned}$  
    
5.  **Objective**  
    模型的目的, 是让(q_{\theta}(x)$的生成概率尽可能大 / 让加噪声和去噪声的过程尽可能相似
      
    
6.  **DDIM to Accelerate Diffusion Process  
    (\begin{aligned} x_t &\sim \mathcal N(\sqrt{1 - \beta_t} x_{t-1}, \beta_t \pmb I) \\ x_t &\sim \mathcal N(\sqrt{\frac{\bar{\alpha}_t}{\bar{\alpha}_{t-1}}} x_{t-1}, \beta_t \pmb I) \\ \end{aligned}$  
    **
7.  可变参数  
    (\alpha_t$可以有不同的初始化策略, cosine更符合生成高分辨率图像的要求
