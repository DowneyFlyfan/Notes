# Fourier Series & Fourier Transform
*   **Fourier Series of Periodic Functions**  
    

1.  **Deduction of Fourier Representation of a Periodic Function  
    ![](paste-dc06a72b535f9f3dc77a252ce2767da41beacdae.jpg)**   
    正弦，余弦函数相互正交，因此可以构成周期内任意周期函数的基底  
    (\begin{aligned} x(t) = \sum^\infty_{k = - \infty} a_k e^{j k \omega_0 t} \\ x\[n] = \sum^\infty_{k = - \infty} a_k e^{j k \dfrac{2\pi}{N} n} \end{aligned}$  
      
    
2.  **Deduction of Fourier Series**  
      
    (\begin{aligned} \int_{- T/2}^{T/2} x(t) e^{-j n \omega_0 t} dt &= \int_{- T/2}^{T/2} a_k e^{j(k-n) \omega_0 t} dt \\ &= a_n T \\ a_k &= \frac{1}{T} \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ a_k &= \frac{1}{T} \sum_{n=0}^T x\[n] e^{-j k \dfrac{2\pi}{N} n} \end{aligned}$

*   **Fourier Transform & Inverse Fourier Transform**  
    

1.  **Fourier Transform**  
    非周期函数可以看成周期无穷大的周期函数  
    (\begin{aligned} T a_k &= \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ X(j k \omega_0) &= \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ X(j \omega) &= \int_{- \infty}^{\infty} x(t) e^{-j \omega t} dt \\ X(e^{j \omega}) &= \sum_{n = -\infty}^{\infty} x\[n]e^{-j \omega n} \end{aligned}$  
    (\because T \rightarrow \infty \Rightarrow \omega_0 \rightarrow 0$, 所以 (k \omega_0$可以看成是整个连续的空间，能表示任意(\omega$  
      
    
2.  Inverse Fourier Transform  
    (\begin{aligned} x(t) &= \sum^\infty_{k = - \infty} a_k e^{j k \omega_0 t} \\ &= \sum^\infty_{k = - \infty} \frac{1}{T} X(j \omega_0 t) e^{j k \omega_0 t} \\ &= \frac{1}{2 \pi} \int_{- \infty} ^{\infty} X(j \omega) e^{j \omega t} d\omega \\ x\[n] &= \frac{1}{2 \pi} \int_{- \infty} ^{\infty} X(e^{j \omega}) e^{j \omega t} d\omega \end{aligned}$  
    

**

*   **2D Fourier Transform  
    (\begin{aligned} \text{1. 2D傅立叶变换公式 (Continuous Case)} \\ F(u, v) &= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y) \cdot e^{-j 2 \pi \left( u x + v y \right)} \, dx \, dy \\ \text{2. 离散傅立叶变换公式 (Discrete Case)} \\ F(u, v) &= \sum_{x=0}^{M-1} \sum_{y=0}^{N-1} f(x, y) \cdot e^{-j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)} \\ \text{3. 逆傅立叶变换公式 (Inverse 2D Fourier Transform)} \\ f(x, y) &= \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} F(u, v) \cdot e^{j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)} \\ \text{4. 离散傅立叶变换的逆变换 (Inverse DFT)} \\ f(x, y) &= \frac{1}{M \cdot N} \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} F(u, v) \cdot e^{j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)} \end{aligned}$  
      
    **
*   **Fourier Transform of common functions  
    (\begin{aligned} \mathcal{F}\left\{ e^{-a x^2} \right\}(\omega) &= \sqrt{\frac{\pi}{a}} \, e^{-\dfrac{\omega^2}{4a}}, a = \frac{1}{2 \sigma^2} \\ \mathcal{F}\left\{ e^{-\frac{x^2}{2\sigma^2}} \right\}(\omega) &= \sigma \sqrt{2\pi} \, e^{-\dfrac{\sigma^2 \omega^2}{2}} \\ F_{Gaussian2d}(\omega_x, \omega_y) &= 2\pi \sigma^2 e^{-\dfrac{\sigma^2(\omega_x^2 + \omega_y^2)}{2}} \end{aligned}$  
      
    **
*   **Inverse Fourier Transform of common functions  
      
    **

**
