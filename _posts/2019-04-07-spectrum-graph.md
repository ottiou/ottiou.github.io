---
layout: post
title:  "代数图论-图谱"
date:   2019-04-07 10:54:49 +0800
categories: math
---
# 图谱
假设$\Gamma$是一个图，他的节点集$V\Gamma$是$\{v_1,v_2,\cdots,v_n\}$，$E\Gamma$将表示$V\Gamma$中无序元素对组成的子集。如果$\{v_i,v_j\}$有一个边连接，我们称$v_i$与$v_j$相邻，因此我们可以定义相邻矩阵：

<strong>定义</strong>：(相邻矩阵)
图$\Gamma$的相邻矩阵是复数域上的一个$n\times n $矩阵 $A=A(\Gamma)$，其中它的每一个元素是
\begin{equation}\notag
a_{i,j}=
\begin{cases}
1& v_i\text{与}v_j\text{相邻},\\\
0& \text{其他}.
\end{cases}
\end{equation}


从定义可以直接得出相邻矩阵是一个实对程矩阵(有向图的话不是)，并且矩阵的迹为0（迹是对角线元素的和，我们知道每个节点自身到自身距离为0，故对角线全是0）。由于图$\Gamma$中节点的下标对应矩阵的行和列，故我们对更关心相邻矩阵的性质，而且矩阵的行列变换不影响矩阵的性质。其中最重要的是矩阵$A$的谱性质。

假设$\lambda$是$A$的一个特征值（即，特征方程$det(\lambda I -A)=0$的根）。由于$A$是实对称矩阵，可知$\lambda$是实数并且$\lambda$的重数与$\lambda$对应特征向量组成的空间的维数相等。

<strong>定义</strong> :(图的谱)
图$\Gamma$的谱是由$A(\Gamma)$的所有特征值和特征值的重数组成的集合。如果$A(\Gamma)$的特征值为$\lambda_0>\lambda_1> \cdots>\lambda_{s-1}$,他们对应的重数为$m(\lambda_0),m(\lambda_1),\cdots,m(\lambda_{s-1})$，则谱为
\begin{equation}\notag
\text{Spec} \ \Gamma=\left (
\begin{matrix}
\lambda_0 & \lambda_1 & \cdots & \lambda_{s-1}\\\
m(\lambda_0) & m(\lambda_1) & \cdots & m(\lambda_{s-1})
\end{matrix}
\right ).
\end{equation}


下面举个例子来说明一下，完备图$K_n$有$n$个节点，并且任意两个节点都是相邻的。即$K_4$对应的相邻矩阵是
\begin{equation}
A=
\begin{bmatrix}
0 & 1 & 1 & 1\\\
1 & 0 & 1 & 1\\\
1 & 1 & 0 & 1\\\
1 & 1 & 1 & 0
\end{bmatrix}
\end{equation}
进而容易计算$K_4$的谱为
\begin{equation}
Spec (K_4) =\left (
\begin{matrix}
3 & -1 \\\
1 & 3
\end{matrix}
\right )
\end{equation}

将用$A(\Gamma)$的特征值来表示图$\Gamma$的特征值。同时，记$A(\Gamma)$的特征多项式为$\chi(\Gamma; \lambda)$，并且也表示图$\Gamma$的特征多项式。 

假设图$\Gamma$的特征多项式为

$$\chi(\Gamma; \lambda) = \lambda^n + c_1 \lambda^{n-1} + c_2 \lambda^{n-2}+\cdots+c_n.$$

则对应的系数$c_i$可以用矩阵$A$主子式的和来解释，因此可以导出如下结论：

<strong>命题</strong>
对于上面提到的多项式的系数$c_i$，有结论：\\
(1) $c_1=0$;\\
(2) $-c_2$是图$\Gamma$的边数;\\
(3) $-c_3$是图$\Gamma$中三角形数量的两倍.


<strong>证明</strong>
对于任意的 $i\in \{1,2,\cdots,n\}$，$(-1)^i c_i$是$A$的所有$i$阶主子式（具有$i$行$i$列）的和。则：\\
(1) 由于A的对角线元素全是0，故$c_1=0$。\\
(2) 对于一个两行两列并且有非零入口的主子式，一定是如下格式：
\begin{equation}
\left|
\begin{array}{cc} 
    0 &  1 \\\
    1 &  0
\end{array}
\right| .
\end{equation}
又每一对相邻节点有一个如此的主子式，并且这个值是$-1$。因此
$(-1)^2 c_2 = - |E\Gamma |$，即得到题设结论。\\
(3) 对于三行三列的非平凡主子式，有如下三种可能：
\begin{equation}
\left|
\begin{array}{ccc} 
    0 & 1 & 0\\\
    1 & 0 & 0\\\
    0 & 0 & 0
\end{array}
\right| ,\ 
\left|
\begin{array}{ccc} 
    0 & 1 & 1\\\
    1 & 0 & 0\\\
    1 & 0 & 0
\end{array}
\right|  ,\ 
\left|
\begin{array}{ccc} 
    0 & 1 & 1\\\
    1 & 0 & 1\\\
    1 & 1 & 0
\end{array}
\right| .
\end{equation}
在这几个主子式中，只有最后一个是非零的（可计算值为2）。满足上述最后一种主子式的节点中，一定对应三个彼此都相邻的节点，即三个节点组成三角形。记三角形的个数为$N_{tri}$，则有$-c_3 = (-1)^3c_3=2N_{tri}$。
$ \blacksquare $

图代数是一个包含图像信息的代数结构。从上文的结果看出，在研究图的代数理论时，图的特征多项式是一个重点的对象。上述只是冰山一角，在文献[1]的第七章将包含更加广泛关于特征多项式系数的内容。

假设$\Gamma$的相邻矩阵是$A$。则在通常的矩阵运算下，$A$中的复系数多项式集构成了一个代数。这个代数是一个有限维的复向量空间。

<strong>定义</strong>（相邻代数）:
图$\Gamma$的相邻代数是相邻矩阵$A=A(\Gamma)$中的多项式的代数。将用$\mathcal{A}(\Gamma)$来表示$\Gamma$的相邻代数。


由于相邻代数的每一个元素是$A$的幂的线性组合，故可以通过研究这些幂来得到关于$\mathcal{A}(\Gamma)$的结论。定义$\Gamma$上长度为$l$从$v_i$到$v_j$的游走，是由$\Gamma$的节点组成的有限序列

$$v_i = u_0,u_1,\cdots, u_l=v_j,$$

并且满足对于$1\le t \le l$，$u_{t-1}$与$u_t$是相邻的。
（如果对于$1\le t \le l$，$u_{t-1}$与$u_{t+1}$是不同的（即不走回头路），则称这个游走是一个路径。）

<strong>引理</strong>
在$\Gamma$中从$v_i$到$v_j$长度为$l$的游走的数量是矩阵$A^l$中位置$(i,j)$的元素的值。

<strong>证明</strong>
对于$l=0$，有$A^0=I$故结论正确。对于$l=1$，$A^1=A$故结论正确。下面假设$l=L$时成立，来考虑$l=L+1$，而有恒等式

$$(A^{L+1})_{ij}=\sum^n_{h=1}(A^L)_{ih}a_{hj}$$

故结论成立。
$ \blacksquare $

在一个连通图中，任意两个节点都可以由一个游走连通。在$\Gamma$中，连接$v_i$和$v_j$的游走中最短游走的边数叫$v_i$到$v_j$的距离，记作$d(v_i,v_j)$。在$\Gamma$中所有距离的最大值，称作$\Gamma$的直径。

<strong>命题</strong>
设$\Gamma$是一个连通图，它的相邻代数为$\mathcal{A}(\Gamma)$，直径是$d$。则$\mathcal{A}(\Gamma)$的维数至少是$d+1$。

<strong>证明</strong>
设$x$和$y$是图$\Gamma$的节点满足$d(x,y)=d$，并且假设

$$x=w_0,w_1,\cdots,w_d=y$$

是一条长度为$d$的路径。
则对于$i\in \{1,2,\cdots,d\}$，至少存在一个长度为$i$的游走连接$w_0$到$w_i$，但是没有更短的游走连接他们了。
因此，$A^i$在某个位置有个非零的元，并且这个位置$I,A,A^2,\cdots,A^{i-1}$对于的元都是$0$;
接着得到，$A^i$与$\{I,A,A^2,\cdots,A^{i-1}\}$不线性相关。
依此可得，$\{I,A,A^2,\cdots,A^{d}\}$ 在 $\mathcal{A}(\Gamma)$中不线性相关，故命题得证。
$ \blacksquare $

图$\Gamma$的谱和相邻代数有着紧密联系。
如果相邻矩阵有$s$个不同的特征值，由于它是实对称矩阵，则它的最小多项式的度是$s$,
因此它的相邻代数的维数也是$s$。
由于不连通图的谱是它的连通部分谱的并，故不失一般性我们将仅仅考虑连通图。
对于不同特征值的数量，有如下的一个上下界。

**推论**
一个具有$n$个节点，直径为$d$的连通图，不同特征值的数量至少是$d=1$，至多为$n$。

在参考文献[1]的最后一部分中一个重要主题是研究具有最少多少不同特征值的图。
这些图有着一些意想不到的规律特性。


<strong>A 连通准则</strong>
一个具有$n$个节点的图是连通的等价于$(A+I)^{n-1}$有非零元（$A$是$\Gamma$的相邻矩阵）。

<strong>B 同谱图 </strong>
对于两个不同构的图，如果他们的特征值相同并且对应的重数相同，则称两个图是同谱的。如下是两个六节点的同谱图，他们的特征多项式是$\lambda^6-7\lambda^4 - 4\lambda^3 + 7\lambda^2 + 4\lambda -1$.\\
![avatar](/Cospectralgraphs1.jpg)

<strong>C 游走生成函数</strong>
设图$\Gamma$的节点集为$\{v_1,v_2,\cdots,v_n\}$，
记$v_{ij}(r)$为连通$v_i$到$v_j$长度是$r$的游走的数量。
如果$N$满足如下

$$N_{ij}=\sum^{\infty}_{r=1}v_{ij}(r)t^r,$$

则$N=(I-tA)^{-1}$，其中$A$是$\Gamma$的相邻矩阵。

<strong>D 特征值的界</strong>
设图$\Gamma$有$n$个节点$m$条边，并且特征值是$\lambda_{1}\ge \lambda_2 \ge \cdots \ge \lambda_{n}$ 。
则$\sum \lambda_i = 0$, $\sum \lambda^2_{i} = 2m$。
对于$(\lambda_2,\cdots, \lambda)$和$(1,1,\cdots,1)$使用Cauchy-Schwarz不等式有
\begin{equation}
\lambda_1\le \Big{(}\frac{2m(n-1)}{n}\Big{)}^{\frac{1}{2}}.
\end{equation}


声明：文章内容是学习文献1的笔记和一些个人看法。个人能力有限难免会有错误和不当，欢迎指正。对于本文表述不清的部分可以参看原书。


# 参考文献

1.Biggs, Norman. Algebraic graph theory. Vol. 67. Cambridge university press, 1993.
