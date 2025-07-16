# Representation Learning
*   **Perception Encoder (25.3)**

1.  Architecture  
    ![](paste-8995fa51a3972b246a197a6638e3c368eb14e8cd.png)![](paste-2499c3861f5d0c09733ed5dc6235adcf6a19d402.png)  
      
    
2.  改进  
    加了**LAMB**(Layer-Wise Moments Optimizer for Large Batch Training): **每层学习率都有缩放**  
    加了**RoPE**  
    加了**数据增强和Masked Regularization**(每个batch取一部分打码，然后丢进去把输出的特征靠齐)  
    **多分辨率训练  
    统一图形模型和视频模型  
      
    **
3.  Insights  
    特征学习的中间层是比输出层更好的特征表示  
    ![](paste-838ef336b04e79fabdc8307c7218490239e6781d.png)
