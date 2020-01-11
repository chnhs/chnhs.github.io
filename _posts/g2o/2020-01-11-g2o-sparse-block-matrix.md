---
layout: post
title: sparse block matrix
categories: g2o
description: 稀疏矩阵及稀疏块矩阵介绍
keywords: optimization
---

# g2o-Sparse Block Matrix(稀疏块矩阵)

![image-20200108002747484](/Users/huangshuai/amap/hs/note/Sparse Block Matrix.assets/image-20200108002747484.png)



## 前言

最近在看 g2o, 想把非线性最小二乘优化问题从它的原理(概率推出)到求解以及最后的实现过一遍. 今天看到了稀疏矩阵块这个部分, 也就是红色标出来的地方. 



## 作用

Sparse Block Matrix 的作用主要是用于存储所构建出来的$H$矩阵, 以及它经过舒尔补之后的矩阵要素.



## 为什么采用稀疏化

稀疏化的作用主要是节约内存, 同时现有的 LinearSolver 库中都支持稀疏矩阵的求解. 详细的总结可以看一下[机器学习-稀疏矩阵的处理 ](http://www.sohu.com/a/289356947_617676).



## g2o 中的压缩方式

g2o 中使用的是行压缩方式(compressed row storage,CRS), 同样对应的还用列压缩方式(compressedcolumn storage,CCS) 以及其他的一些压缩方式. 关于样例介绍及实现请参考[稀疏矩阵的三元组表示方式](https://blog.csdn.net/qq_35733751/article/details/80843589).



## 什么叫稀疏块矩阵

刚开始看的时候有点懵, 不过看到 slam++中有一个详细的介绍. 链接如下 [Block Matrix]([https://sourceforge.net/p/slam-plus-plus/wiki/Block%20Matrix/](https://sourceforge.net/p/slam-plus-plus/wiki/Block Matrix/)). 大白话就是稀疏矩阵与块表示的结合, 因为我们待优化参数的自由度是确定的, 在构造优化问题时我们也能够将数量确定下来,  这时候我们就能够确定spare block matrix 的大小以及 Block 的大小.



## Reference

[1] http://www.sohu.com/a/289356947_617676

[2]https://blog.csdn.net/qq_35733751/article/details/80843589

[3]https://sourceforge.net/p/slam-plus-plus/wiki/Block%20Matrix/](https://sourceforge.net/p/slam-plus-plus/wiki/Block Matrix/

