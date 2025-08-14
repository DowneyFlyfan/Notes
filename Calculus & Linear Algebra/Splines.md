# **Splines**
*   from **lerp(Linear Interpolatipon)** to **Bezeir  
      
    Lerf:** (P(t) = (1 - t) P_0 + tP_1$  
      
    **Cubic Bezeir  
    ![](paste-aecc65b305961f5bd6a78dc83f0c5151312bf8dc.jpg)  
      
    12-Degree Bezeir: No local control, computational expensive, doesn't pass most points**  
    ![](paste-63cfd1070404a1b18feb296068298ae1baab7a09.jpg)  
      
    
*   **Hermite Splines**  
    知道一个三次曲线的两点坐标和斜率，可以求出这个曲线  
    ![](paste-158028fd09924c429c498d8bbcdccaecc5a331b8.jpg)  
    特点: Explicit Derivative; Interpolating (经过每一个插值点); (C^{(1)}$Continuous  
      
    **Hermite to Bezeir  
    **![](paste-321a67c83747d1f568a01e923150d10b8ead968d.jpg)  
      
    
*   **Cardinal Spline & Catmull-Rom Spline**  
    用1,3点的向量作为插值点2的方向向量并进行缩放来增加平滑性  
    当(Scale = 0.5$时，被称作Catmull-Rom Spline  
      
    ![](paste-13c8b658b62f6daaffbde7fd303dff6f274ff994.jpg)  
    Expression when (s = 1/2$: ![](paste-86712b271f014333f3a5924e90d55c9441d51786.jpg)  
      
    
*   **Cubic B-Spline & B-Spline  
      
    Cubic B-Spline**  
    为了使得 Catmull-Rom Spline (C^{(2)}$连续  
    ![](paste-09030463489af811b701b02271b9c0e03147e575.jpg)  
    可以得到![](paste-9b5bad60a822c39702d80028e843aa4fa8db36f7.jpg)  
      
    **B-Spline  
      
    (\begin{aligned} B_{i,k}(t) &= \alpha_{i, k-1} B_{i, k-1}(t) + (1 - \alpha_{i+1, k-1}) B_{i+1, k -1}(t) \\ &= \frac{t - t_i}{t_{i+k} - t_i} B_{i, k-1}(t) + \frac{t_{i +k + 1} - t}{t_{i + k + 1} - t_i} B_{i+1, k-1}(t) \\ i &: Index \ of \ knots \ vectors; \ k: Order \end{aligned}$  
    **
