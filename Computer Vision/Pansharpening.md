---
id: Pansharpening
aliases: []
tags:
  - CV
  - flashcards
---

# Traditional Methods

## MRA (Multi-Resolution Analysis)  

 MRA 方法的全称是什么？ :: Multi-Resolution Analysis

1. 加法

$$
\begin{equation}
\begin{aligned}
I_E &= I_{LMS} + g (P_{match} - P_{match}^{lp}) 
\end{aligned}
\end{equation}
$$

- 然后在$g$上下功夫
      
2. 乘法

$$
\begin{equation}
\begin{aligned}
I_E &= I_{LMS} \times \frac{P_{match}}{P_{match}^{lp}} 
\end{aligned}
\end{equation}
$$

3. 能不能融合一下???

- **TODO**

## LRTCF (Low-Rank Tensor Completion-Based Framework)  

$$
\begin{equation}
\begin{aligned}
X & =X \otimes B + g_{new} (P^{hist} - P_{low-pass}^{hist}) \\ g_{new} &= \frac{X - X \otimes B}{ P^{hist} - P_{low-pass}^{hist}} \\ &= \frac{[(X - X \otimes B) \otimes B] \downarrow_r}{ [(P^{hist} - P_{low-pass}^{hist}) \otimes B] \downarrow_r} \\ &= \frac{ y - [X \otimes B \otimes B] \downarrow_r}{\widehat P^{hist} - \widehat P_{low-pass}^{hist}} \\ &\approx \frac{ y - y \otimes B}{\widehat P^{hist} - \widehat P_{low-pass}^{hist}} \\ &= \frac{ (y - y \otimes B) (\widehat P^{hist} - \widehat P_{low-pass}^{hist}) }{|| \widehat P^{hist} - \widehat P_{low-pass}^{hist}||^2}
\end{aligned}
\end{equation}
$$

- 然后把$g_{new}$上采样后放到网络里学习可以得到不错的初始化，收敛迅速
    
## MTF

### 经验
    
1. 模糊核**不一定是高斯形状**的

2. 传感器在卫星运动方向和垂直于运动方向和速度不一样, 所以模糊核不应是绝对对称的

3. 传感器老化以后**Nyquist Gain**就变了  

### Multi-Band Filter Estimation (MBFE)

1. 估计模糊核

$$
\begin{equation}
\begin{aligned}
\mathbf{p}_e = \widetilde{\mathbf{M}}^T \boldsymbol{\alpha}' \\
\underset{\mathbf{h}, \boldsymbol{\alpha}}{\text{minimize}} & \{ \| \mathbf{p}_e - \mathbf{P}_C \mathbf{h} \|^2 + \lambda \| \mathbf{h} \|^2 + \mu (\| \mathbf{D}_v \mathbf{h} \|^2 + \| \mathbf{D}_h \mathbf{h} \|^2) \} \\
\text{subject to} & \ \mathbf{h}^T \mathbf{1} = 1, \mathbf{h} \in \mathcal{H}
\end{aligned}
\end{equation}
$$

- 第二个公式解答后改成傅里叶变换会更快

2. 按比例注入细节

$$
\begin{equation}
\begin{aligned}
I_{E} &= I_{LMS} \times \frac{P_{match}}{P_{match}^{lp}} 
\end{aligned}
\end{equation}
$$

### $Gau \beta$

| Variable | Description |
|---|---|
| $r$ | ratio |
| $N$ | kernel size |
| $G$ | Nyquist Gain |
| $h$ | Frequency Response |
| $H_t$ | Time Response |
| $FS$ | Frequency Shift |

- For **Each Channel**

$$
\begin{equation}
\begin{aligned} 
\sigma &= \sqrt{-\frac{(N-1)^2}{8r^2 \ln G}} = \frac{N-1}{2r} \sqrt{-\dfrac{1}{2 ln G} }   \\ 
h &= e^{-\dfrac{x^2 + y^2}{2\sigma^2}} \rightarrow h = \frac{h}{\sum_{i=1}^{HW} h } \rightarrow h = \frac{h}{\max(h)} \\ 
k &= \frac{I_0(\beta \sqrt{1 - \dfrac{4 n^2}{(N-1)^2}})}{I_0(\beta)}, -\frac{N-1}{2} \le n \le \frac{N-1}{2} \\ 
H_t &= h \rightarrow rotate \ 180^0 \rightarrow FS \rightarrow rotate \ 180^0 \rightarrow IFFT \rightarrow FS \rightarrow rotate \ 180^0 \\ 
& \rightarrow h \times k \rightarrow relu(h) \rightarrow \frac{H_t}{\sum_{i=1}^{HW} H_t}.real 
\end{aligned}
\end{equation}
$$

## OMP(Orthogonal Match Pursuits)

| Variable | Description |
|---|---|
| $y = y - MTF(y)$ | LRMS Detail |
| $\widehat{P}$ | PAN histogram matched to LMS |
| $D_h$ | $\widehat{P} - MTF(\widehat{P})$ |
| $D_l$ | $MTF(D_h) ,4 \times \downarrow$ |
| $X$ | HRMS |

- Then $y, D_l, D_h$ are **patchified** with $stride=7 \times  ratio,overlap=4 \times ratio$

```py
for i in range(10):
    res = y
    D_li = min dist(res, D_l)
    # get alpha by lstsq(D_l, y)[0]
    # y (nc, hw) = D_l (nc, hw, i) alpha (nc, i) \\
    res = y - D_l alpha
```

- Then, $X = D_h \alpha$

# Indications \& Loss Functions

| Variable | Description |
|---|---|
| $a$ | $\in \mathcal R^{1 \times C \times H \times W}$ |
| $b$ | $\in \mathcal R^{1 \times C \times H \times W}$ |
| $patch_a$ | $\in \mathcal R^{hw \times c \times p \times p}$ |
| $patch_b$ | $\in \mathcal R^{hw \times c \times p \times p}$ |

### Indexes

$$
\begin{equation}
\begin{aligned}
PSNR &= 10 \frac{1}{BC}\sum_{i=1}^{BC} \lg \frac{1}{\dfrac{1}{HW}\sum_{j=1}^{HW}(a-b)^2} \\ 

SAM &= \sum_{i=1}^{BHW} \cos^{-1}\Big[ \frac{\sum_{i=1}^C a \times b}{\sqrt{\sum_{i=1}^C a^2 \times \sum_{i=1}^C b^2}} \Big] \\ 

ERGAS &= \frac{1}{B} \sum_{i=1}^B \frac{100}{ratio} \times \sqrt{\sum_{j=1}^C\frac{\sum_{m=1}^{HW}(a-b)^2} {(\sum_{i=1}^{HW}a)^2} / channel} \\

SSIM &= \frac{4(I_1 \otimes k)(I_2 \otimes k)[I_1I_2 \otimes k - (I_1 \otimes k)(I_2 \otimes k)]}{[(I_1 \otimes k)^2 + (I_2 \otimes k)^2] [I_1^2 \otimes k + I_2^2 \otimes k -(I_1 \otimes k)^2 - (I_2 \otimes k)^2]} \\ 

CC &= \frac{1}{BC} \sum_{i=1}^{BC}\frac{\sum_{i=1}^{HW} ab - \sum_{i=1}^{HW} a \sum_{i=1}^{HW} b}{\sqrt{ \Big[\sum_{i=1}^{HW} b^2- \dfrac{1}{HW}(\sum_{1}^{HW}b)^2\Big] \Big[\sum_{i=1}^{HW} a^2- \dfrac{1}{HW}(\sum_{1}^{HW}a)^2\Big]}} \\ 

D_s &= \underbrace{\frac{2\bar{x}\bar{y}}{(\bar{x}^2 + \bar{y}^2)}}_{\text{Luminance } L(x, y)} \cdot \underbrace{\frac{2\sigma_x \sigma_y}{(\sigma_x^2 + \sigma_y^2)}}_{\text{Contrast } C(x, y)} \cdot \underbrace{\frac{\sigma_{xy}}{\sigma_x \sigma_y}}_{\text{Structure } S(x, y)} \\
&= \frac{4\sigma_{xy}\bar{x}\bar{y}}{(\sigma_x^2 + \sigma_y^2)(\bar{x}^2 + \bar{y}^2)}
\end{aligned}
\end{equation}
$$

1. 其中, $D_s$ 会逐patch计算取平均值

2. $D_{\lambda}^k$用了超复数模计算，全部算均值，没有方差

3. **HQNR**

- $I_{fuse} \otimes k$跟$LMS$比$D_{\lambda}^k$

- $I_{fuse} \otimes k$跟$LMS$比Q Index; $PAN$下采样再上采样，跟$LMS$比Q Index

- 两个Q Index相差取绝对值就是$D_s$

### Loss Functions

1. 我发明的针对**Zero-shot**的Loss, 配合**高学习率**使用

$$
\begin{equation}
\begin{aligned}
QSE &= \sum_{i=1}^C\sqrt{\sum_{i=1}^{BHW} \sqrt{\sum_{i=1}^{p^2} (patch_a-patch_b)^2}} \\ 
PW-SAM &= \sum_{i=1}^{BHW} \cos^{-1}\Big[  \frac{1}{p^2} \sum_{i=1}^{p^2} \frac{\sum_{i=1}^C a \times b}{\sqrt{\sum_{i=1}^C a^2 \times \sum_{i=1}^C b^2}} \Big]
\end{aligned}
\end{equation}
$$
      
# 经验之谈  
    
1. ***replicate填充*** 最适合 **pansharpening, 超分**等任务
