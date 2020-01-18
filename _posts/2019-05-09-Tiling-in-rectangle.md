---
layout: post
title:  "矩形内平铺定位问题"
date:   2019-05-09 19:55:08 +0800
categories: AI and Math
---
# 矩形内平铺定位问题

## 矩形内平铺问题
- 1.给定一个集合$E=\\{r_1,r_2,\cdots,r_n\\}$，包含$n$个矩形，设第$i$个矩形的长和宽为$l_i$和$w_i$，再给一个大矩形$R$长宽为$L,W$。假设他们满足关系$\sum_{i=0}^{n}l_i\times w_i = L\times W$,试问能否将$E$中的矩形平铺到$R$内，即每个小矩形在大矩形内部，并且彼此互不相交。可以设计算法来实现，要求算法复杂度尽可能低。

- 2.问是否一个简单代数等式$eq$使得集合满足$eq$则可以平铺，否则不可(即等价条件)。


## 矩形内定位问题
- 3.如上面问题描述，一堆小矩形平铺在大矩形内，并且不留余地，以大矩形左小角建立坐标系，给定矩形内一点$P=(x,y)$的坐标，如何让快速确定这个点$P$在哪个小矩形内？
- 4.如果对小矩形按照从左向右，从下向上排好序，是否有更快的算法？