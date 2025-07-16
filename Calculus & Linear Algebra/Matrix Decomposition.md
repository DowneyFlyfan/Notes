# **Matrix Decomposition**
*   _**Characteristic Value & Decomposition**_  
    

1.  **公式**  
    (Ax = \lambda x, A \in R^{n \times n}$**,** (\lambda$**: Characteristic Value,** (x$**: Characteristic Vector**(W = Norm_{p-2}(\[ x_1 , .... x_n]) \Rightarrow WW^T = I, \sum = \pmatrix{ \lambda_1 & 0 & ... \\ 0 & \lambda_2 & ... \\ 0 &... & \lambda_n }$**,  
    那么有**(A = W \sum W^T = \lambda x x^T$  
      
    
2.  **几何意义:**  
    特征向量表示经过矩阵(A$变换后方向不变(或相反)的向量，即**矩阵的方向**  
    特征值表示向量模长的缩放比例  
    

*   _**Singular Value Decomposition**_  
    

1.  **分解**  
    (A \in R^{m \times n} = U \sum V^T$  
    (U \in \mathcal R^{m \times m}$: Left-Singular Vector Matrix  
    (V \in \mathcal R^{n \times n}$: Right-Singular Vector SMatrix  
    (\sum \in \mathcal R^{m \times n}$: Singular Value Matrix  
    (A^T A v_i = \lambda_i v_i, AA^T u_i = \lambda_i u_i$  
      
    
2.  **方阵的奇异值和特征值的关系  
    **(\begin{aligned} A^T &= (U \sum V^T)^T = V \sum^T U^T \\ A^T A & = V \sum^T U^T U \sum V^T \\ &= V (\sum)^2 V^T \\ \therefore \sigma_i &= \sqrt{\lambda_i} \end{aligned} $
