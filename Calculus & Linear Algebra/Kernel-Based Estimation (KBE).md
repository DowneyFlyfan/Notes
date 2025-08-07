# Kernel-Based Estimation (KBE)
*   估计直方图

1.  生成(\[0,1]$的**均匀递增序列，长度为**(num_{bins}$, 作为**均值**(\mu$代入(f(x | \mu, \sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$, 得到(num_{bins}$个高斯分布
2.  将patches((bsz, num_{pixels})$作为**输入**(x$代入以上高斯分布, 得到**kernel**((bsz, num_{pixels}, num_{bins}$)
3.  在(dim=1$上取均值得到pdf((bsz, num_{bins})$，含义为: **用所有数据点离这个点的距离(1最大，0最小)代替离散的统计，达到平滑的效果  
    **
4.  对pdf归一化, 得到**直方图**
