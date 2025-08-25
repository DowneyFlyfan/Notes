---
id: Graph
aliases: []
tags:
  - Coding
---


# 图论算法
*   匈牙利算法  
    **问题描述**: n个人做n件事, 让成本最小的工作分配方式  
    **解决方法**: 每行去掉最小值 (\rightarrow$ 每列去掉最小值 (\rightarrow$ 用尽可能少的直线实现零元素覆盖 (\rightarrow$ 减去未覆盖元素的最小值，给覆盖元素加上这个最小值 (\rightarrow$ 循环直至找到最佳分配
