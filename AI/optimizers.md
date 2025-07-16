
"

* SGD(Stochastic Gradient Descent)

1. 参数更新公式： (v_t = \gamma v_{t-1} + \eta \nabla_{\theta} J(\theta), \theta_t = \theta_{t-1} - v_t$  
     
    (v$是动量，(\gamma$是动量参数（一般接近1），(\eta$是学习率，(J(\theta)$是损失函数
2. 代码见 LARS部分

* Adam (Adaptive Momentum Estimation)

1. Update Function for Parameters  
     
   (\begin{gather}

---
