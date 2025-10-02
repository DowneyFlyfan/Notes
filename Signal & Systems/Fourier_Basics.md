---
id: Fourier_Basics
aliases: []
tags:
  - Math
---

# Fourier Series & Fourier Transform

## Fourier Series of Periodic Functions
   
1.  **Deduction of Fourier Representation of a Periodic Function**

$$
\begin{equation}
\begin{aligned}
\int_{-\pi}^{\pi} \cos(mt) \sin(nt) dt &= 0 \\
\int_{-\pi}^{\pi} \cos(mt) \cos(nt) dt &= 0, m \neq n \\
\int_{-\pi}^{\pi} \sin(mt) \sin(nt) dt &= 0, m \neq n \\
\end{aligned}
\end{equation}
$$

- **正余弦函数相互正交**，因此可以构成周期内任意周期函数的基底  

$$
\begin{equation}
\begin{aligned}
x(t) &= \sum^\infty_{k = - \infty} a_k e^{j k \omega_0 t} \\ 
x[n] &= \sum^\infty_{k = - \infty} a_k e^{j k \dfrac{2\pi}{N} n}
\end{aligned}
\end{equation}
$$

2. **Deduction of Fourier Series**  

$$
\begin{equation}
\begin{aligned}
\int_{- T/2}^{T/2} x(t) e^{-j n \omega_0 t} dt 
&= \int_{- T/2}^{T/2} a_k e^{j(k-n) \omega_0 t} dt \\ 
&= a_n T
\end{aligned}
\end{equation}
$$

- 只有在$k = n$时，右式才有值

$$
\begin{equation}
\begin{aligned}
a_k &= \frac{1}{T} \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ 
a_k &= \frac{1}{T} \sum_{n=0}^T x[n] e^{-j k \dfrac{2\pi}{N} n}
\end{aligned}
\end{equation}
$$
      
## Fourier Transform & Inverse Fourier Transform
    
1.  **Fourier Transform**  

- 非周期函数可以看成周期无穷大 ($T \xrightarrow{} \infty, \omega_0 \xrightarrow{} 0$) 的周期函数

$$
\begin{equation}
\begin{aligned}
T a_k &= \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ 
X(j k \omega_0) &= \int_{- T/2}^{T/2} x(t) e^{-j k \omega_0 t} dt \\ 
X(j \omega) &= \int_{- \infty}^{\infty} x(t) e^{-j \omega t} dt \\ 
X(e^{j \omega}) &= \sum_{n = -\infty}^{\infty} x[n]e^{-j \omega n}
\end{aligned}
\end{equation}
$$

- 所以$k \omega_0$可以看成是整个连续的空间，能表示任意$\omega$

2. Inverse Fourier Transform  

$$
\begin{equation}
\begin{aligned}
x(t) &= \sum^\infty_{k = - \infty} a_k e^{j k \omega_0 t} \\
&= \sum^\infty_{k = - \infty} \frac{1}{T} X(j k \omega_0) e^{j k \omega_0 t} \\
&= \frac{1}{2 \pi} \int_{- \infty} ^{\infty} X(j \omega) e^{j \omega t} d\omega \\
x[n] &= \frac{1}{2 \pi} \int_{- \infty} ^{\infty} X(e^{j \omega}) e^{j \omega t} d\omega
\end{aligned}
\end{equation}
$$

## 2D Fourier Transform

1. Transforms

$$
\begin{equation}
\begin{aligned}
F(u, v) &= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x, y) \cdot e^{-j 2 \pi \left( u x + v y \right)} \, dx \, dy \\
F(u, v) &= \sum_{x=0}^{M-1} \sum_{y=0}^{N-1} f(x, y) \cdot e^{-j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)} \\
f(x, y) &= \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} F(u, v) \cdot e^{j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)} \\
f(x, y) &= \frac{1}{M \cdot N} \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} F(u, v) \cdot e^{j 2 \pi \left( \frac{u x}{M} + \frac{v y}{N} \right)}
\end{aligned}
\end{equation}
$$

2. **2D Fourier Transform of Common functions**

$$
\begin{equation}
\begin{aligned}
\mathcal{F}\left\{ e^{-a x^2} \right\}(\omega) &= \sqrt{\frac{\pi}{a}} \, e^{-\dfrac{\omega^2}{4a}}, a = \frac{1}{2 \sigma^2} \\
\mathcal{F}\left\{ e^{-\frac{x^2}{2\sigma^2}} \right\}(\omega) &= \sigma \sqrt{2\pi} \, e^{-\dfrac{\sigma^2 \omega^2}{2}} \\
F_{Gaussian2d}(\omega_x, \omega_y) &= 2\pi \sigma^2 e^{-\dfrac{\sigma^2(\omega_x^2 + \omega_y^2)}{2}}
\end{aligned}
\end{equation}
$$

## Fast Fourier Transform(FFT)

$$
\begin{equation}
\begin{aligned}
y(t) &= x(t) \otimes h(t) \xLeftrightarrow{FT}  Y(j \omega) = X(j \omega) \cdot H(j \omega) \\
y(t) &= IFFT \Big\{ Y(j \omega) \Big\}
\end{aligned}
\end{equation}
$$

- 把一个长度为$N$(最好是2的倍数)的序列**按二分法一直拆到长度为2**为止, 每个部分分别进行**DFT**, 得到$X(j \omega)$和$H(j \omega)$
