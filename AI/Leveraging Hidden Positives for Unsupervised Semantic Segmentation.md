# Leveraging Hidden Positives for Unsupervised Semantic Segmentation
*   结构  
    

1.  GHP (Global Hidden Postiives)  
    ![](paste-133dfabe61dba7044365c245d0f7d57bc54a5948.jpg)  
    两个样本之间的相似度 > 每个样本与池子中的样本的最大相似度， 就归类为positives  
    ![](paste-ccca5803d8c0ea1ce840a4f6c9ea8c6ac0456c86.jpg)![](paste-a46fec2c13fcf55738f515899bf2c6309bf18ba6.jpg)  
    用Postive, negative 和 projection 对agnostic/specific task 分别算一个 Cross Entropy loss  
      
    
2.  LHP (Local Hidden Positives)  
    ![](paste-758d97d031bcf4b53b4c5143389bf648ca92889c.jpg)  
    ![](paste-9728daa5076a4e54c133f60bc669127563e20804.jpg)![](paste-7f854c6b5d4bc528bc59af124164d34e101ff0ef.jpg)  
    ![](paste-ff89282ecb1ee4b97783368b7a06b3abc0622c6c.jpg)![](paste-664b526f46b3acc5845fb026d2e5c96deb17de9d.jpg)  
    超过平均值的 attn_score 和像素的加权平均的缩放投影到 z 再做cross_entropy loss  
      
    
3.  Final Loss  
    ![](paste-136fb6cae30249ae4d84802caac7fd1e9606160f.jpg)  
    

*   结论  
    

1.  优点: 分类更平滑  
      
    
2.  缺点: 超参太多，要专门调控
