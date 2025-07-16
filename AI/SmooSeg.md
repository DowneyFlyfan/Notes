*   文章背景 ( What + Why )

1.  监督学习打标签费时费力  
    
2.  已知的图像先验知识:  
      
    Semantic Consistency: 不管图像进行何种变换，其标签应当是不变的  
      
    Prior Concepts:  
    CRF 强调每个图片内的 local smoothness,  
    STEGO 些许不同就会导致图像分类不同 (对图像分类过于敏感)  
    SmooSeg 连续性更强  
      
    Smoothness Prior: 同一个标签内的像素是连续和平滑的，不同标签之间的像素是不连续的，divergent的  
    

*   Method (How)

1.  问题描述  
    ![](paste-96e17f29f6d3011cd315e88fc008cdc7bb4eace0.jpg)  
      
    
2.  网络结构  
    ![](paste-9db8137bf8303dc844664ba6cb7f398d028db33b.jpg)  
      
    
3.  Loss Function  
    Smoothness Prior  
    ![](paste-197f7fc60e78ebec4a48aad2aff86ec371254701.jpg)  
    ![](paste-acc40020221ceb0855f9465e8460d4449e4152b1.jpg)![](paste-eab36a5dfa20f63dd8a3befa3a769179b158b18c.jpg)![](paste-f77accf3b58af2f390b03ca2db40cf74fc4149fa.jpg)  
    {\[Cosine Similarity ( With zero BN) - Bias ] \* Label Penalty} (Add both within Image & across Image)  
      
    Label Assignments  
    ![](paste-11a87773f297f875310f89b77191229c0feef7ae.jpg) (Z 和 P 都PreNorm)  
    Data Energy  
    ![](paste-20137312345649b87e08a1985183bbe7b8a3cd6e.jpg)![](paste-ec2d85842aaf8305abe70ebcb8eee696d40d7b9c.jpg)  
      
    Final Loss  
    ![](paste-f8190c921b9f81ca07cf1cfabe1a04722a45a6ce.jpg)  
      
    Backward Propogation: (P^s$只用(E_{data}$更新, (P^t$只用EMA更新, Projector 只用 (E_{smooth}$更新  
      
    
4.  Ablation Study  
    ![](paste-2f34daaccd8488c8e4179c36f3ced7267106341e.jpg)  
    (\tau \rightarrow 0, \alpha \rightarrow 1$最好, (E_{smooth}$最重要，(E_{data}$必须结合Teacher 和 Student 才能产生好的表现  
      
    
5.  Appendix  
    Hyper Params Selection:  
    ![](paste-7623051ba1d7eb834a60bf6d6087b600f55669d6.jpg)  
    根据Smoothness 选择 (b_1, b_2$
