# Pansharpening Summary
*   MRA ( Multi-Resolution Analysis)  
    (\begin{align} GT &= LMS + g (P^{repeat} - P_{low-pass}) \\ g &= \frac{LMS}{P_{low-pass}} \end{align}$  
    但是这个方法不够准  
      
    
*   LRTCF (Low-Rank Tensor Completion-Based Framework)  
    (\begin{aligned} X & =X \otimes B + g_{new} (P^{hist} - P_{low-pass}^{hist}) \\ g_{new} &= \frac{X - X \otimes B}{ P^{hist} - P_{low-pass}^{hist}} \\ &= \frac{\[(X - X \otimes B) \otimes B] \downarrow_r}{ \[(P^{hist} - P_{low-pass}^{hist}) \otimes B] \downarrow_r} \\ &= \frac{ y - \[X \otimes B \otimes B] \downarrow_r}{\widehat P^{hist} - \widehat P_{low-pass}^{hist}} \\ &\approx \frac{ y - y \otimes B}{\widehat P^{hist} - \widehat P_{low-pass}^{hist}} \\ &= \frac{ (y - y \otimes B) (\widehat P^{hist} - \widehat P_{low-pass}^{hist}) }{|| \widehat P^{hist} - \widehat P_{low-pass}^{hist}||^2} \\ \end{aligned}$  
      
    然后把(g_{new}$上采样后放到网络里学习可以得到更好的结果, 且收敛迅速  
      
    
*   MTF  
    

1.  模糊核**不一定是高斯形状**的
2.  传感器在卫星运动方向和垂直于运动方向是不对称的(速度不一样), 这样就**不是对称的高斯分布  
    **
3.  传感器老化以后**Nyquist Gain就变了  
    **
4.  **使用Nyquist Gain 获得 MTF 模糊核  
    **  
    (\begin{aligned} r &: ratio, N: kernel \ size \\ G &: Nyquist \ Gain, h: Frequency \ Response \\ H_t &: Time \ Response (Kernel), FS: Frequency \ Shift \\ \sigma &= \sqrt{-\frac{(N-1)^2}{8r^2 \ln G}} \\ h &= e^{-\dfrac{x^2 + y^2}{2\sigma^2}} \rightarrow h = \frac{h}{\sum_{i=1}^{HW} h } \rightarrow h = \frac{h}{\max(h)} \\ k &= \frac{I_0(\beta \sqrt{1 - \dfrac{4 n^2}{(N-1)^2}})}{I_0(\beta)}, -\frac{N-1}{2} \le n \le \frac{N-1}{2} \\ H_t &= h \rightarrow rotate \ 180^0 \rightarrow FS \rightarrow rotate \ 180^0 \rightarrow IFFT \rightarrow FS \rightarrow rotate \ 180^0 \\ & \rightarrow h \times k \rightarrow clip(0, max) \rightarrow \frac{H_t}{\sum_{i=1}^{HW} H_t}.real \end{aligned}$  
    
*   指标和损失函数  
      
    (\begin{aligned} a & \in \mathcal R^{1 \times C \times H \times W}, b: \in \mathcal R^{1 \times C \times H \times W} \\ patch_a & \in \mathcal R^{hw \times c \times p \times p}, patch_b \in \mathcal R^{hw \times c \times p \times p} \\ PSNR &= 10 \frac{1}{BC}\sum_{i=1}^{BC} \lg \frac{1}{\dfrac{1}{HW}\sum_{j=1}^{HW}(a-b)^2} \\ SAM &= \sum_{i=1}^{BHW} \cos^{-1}\Big\[ \frac{\sum_{i=1}^C a \times b}{\sqrt{\sum_{i=1}^C a^2 \times \sum_{i=1}^C b^2}} \Big] \\\ ERGAS &= \frac{1}{B} \sum_{i=1}^B 100 \times ratio\times \sqrt{\sum_{j=1}^C\frac{\sum_{m=1}^{HW}(a-b)^2} {(\sum_{i=1}^{HW}a)^2} / channel} \\ SSIM &= \frac{4(I_1 \otimes k)(I_2 \otimes k)\[I_1I_2 \otimes k - (I_1 \otimes k)(I_2 \otimes k)]}{\[(I_1 \otimes k)^2 + (I_2 \otimes k)^2] \[I_1^2 \otimes k + I_2^2 \otimes k -(I_1 \otimes k)^2 - (I_2 \otimes k)^2]} \\ CC &= \frac{1}{BC} \sum_{i=1}^{BC}\frac{\sum_{i=1}^{HW} ab - \sum_{i=1}^{HW} a \sum_{i=1}^{HW} b}{\sqrt{ \Big\[\sum_{i=1}^{HW} b^2- \dfrac{1}{HW}(\sum_{1}^{HW}b)^2\Big] \Big\[\sum_{i=1}^{HW} a^2- \dfrac{1}{HW}(\sum_{1}^{HW}a)^2\Big]}} \\ Q2n &= \sqrt{ \sum_{\text{blocks}} \left( \frac{2 \cdot \text{cov}(\mathbf{B}_{\text{gt}}, \mathbf{B}_{\text{pred}}) \cdot \gamma}{\sigma_{\text{gt}}^2 + \sigma_{\text{pred}}^2} \right)^2 }, \gamma = \frac{2 \cdot \|\mu_{\text{gt}}\| \cdot \|\mu_{\text{pred}}\|}{\|\mu_{\text{gt}}\|^2 + \|\mu_{\text{pred}}\|^2} \\ NMSE &= \sum_{i=1}^C\sqrt{\sum_{i=1}^{Bhw} \sqrt{\sum_{i=1}^{p^2} (patch_a-patch_b)^2}} \\ PW-SAM &= \sum_{i=1}^{Bhw} \cos^{-1}\Big\[ \sum_{i=1}^{p^2} \frac{\sum_{i=1}^C a \times b}{\sqrt{\sum_{i=1}^C a^2 \times \sum_{i=1}^C b^2}} \Big] \end{aligned}$  
      
      
    PWMSE 是针对单图训练**十分有效的**
*   经验之谈  
    

1.  replicate 填充最适合**pansharpening, 超分**等任务
