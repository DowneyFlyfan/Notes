---
id: Traditional CNNs
aliases: []
tags:
  - AI
---

| Convolution Type           | Description                                                                                                                                                                                                                                                                       |
| :------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard / Full Convolution | $(C_{out} \times C_{in} \times K \times K)$ 的卷积核**和每一个通道卷积得到一个通道输出**，多次卷积后得到想要的输出通道数                                                                                                                                                            |
| nn.Conv3d                  | 对于视频 (Channel \* Depth \* Height \*Width) 等有很大帮助。使用3维卷积核在3个方向上滑动卷积。                                                                                                                                                                                           |
| nn.Conv1d                  | (kernel.shape = $(C_{out}, C_{in}, K)$, 同样是**双向打padding**                                                                                                                                                                                                                    |
| Point-Wise Convolution     | 使用 $(1 \times 1)$ 卷积核在每个像素点的所有通道上进行卷积 (只对通道维度进行卷积)                                                                                                                                                                                                      |
| Depth-Wise Convolution     | 使用 $(K \times K)$ 的卷积核对每一个通道进行卷积，**输出通道数 = 输入通道数**，但是输出的通道之间**缺乏相关性**。`self.depthwise_conv = nn.Conv2d(in_channels, in_channels, kernel_size=kernel_size, padding=padding, groups=in_channels)` # Groups 为输入通道数 |
| BSConv (Blueprint Saparable Convolution) | PW-Conv -> DW-Conv                                                                                                                                                                                                                                                |
| SpanConv                   | PW-Conv \*2 -> DW-Conv (增加了矩阵的秩)                                                                                                                                                                                                                                           |
| Group Convolution          | **groups** 必须能同时被 $(C_{in})$ 和 $(C_{out})$ 整除，等于把整个图像分割成**groups个**卷积                                                                                                                                                                                      |
| Dilation Convolution (空洞卷积) | 跳跃式采样，增加感受野。dilation = 1 为普通卷积, dilation = 2 产生下图效果。![](paste-02a2afa8ba0330e8b8f7a6b088d3c5127
