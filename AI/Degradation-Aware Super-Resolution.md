# Degradation-Aware Super-Resolution
1.  网络结构  
    ![](paste-40931a10283aa489bd4da5766fb5170dd3870d70.jpg)  
    
2.  Loss  
    ![](paste-e1b474744b1c5c6487e0821c65469e8ec1982a6a.jpg) + L1 Loss (HR 和 SR image之间)  
      
    
3.  所有的LR image是由(I_{HR} \otimes k$得到的, (k$是根据具体任务进行选择的
