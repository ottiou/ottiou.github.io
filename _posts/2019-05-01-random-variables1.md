---
layout: post
title:  "统计分析-随机变量1"
date:   2019-05-01 22:27:55 +0800
categories: math
---
# 统计分析-随机变量

## 1.基础例子
首先介绍一些概率中的基本例子。
一个最常见的例子就是抛硬币：将硬币抛出，得到正面和反面的概率都是$1/2$.
如果独立的进行$n$次抛投，则$n$次全是正面的概率是$1/2^n$:
由于有$2^n$种可能等可能的结果，但仅仅一种全是正面。
跟一般，设$S_n=X_1+X_2+\cdots+X_n$，其中
\begin{equation}\notag
X_j=
\begin{cases}
1, \text{第}j\text{次为正面},\\\
0, \text{第}j\text{次为反面}.
\end{cases}
\end{equation}
则$n$次投递后得到$k$个正面的概率是：
\begin{equation}\notag
\text{Prob}(S_n=k)=\frac{1}{2^n} {n\choose k}
\end{equation}
通过Stirling公式，
\begin{equation}
n!\sim \sqrt{2\pi n}(\frac{n}{e})^n,\ \ n\to \infty
\end{equation}
例如可以计算获得正面刚好是总次数一半的渐近概率为
\begin{equation}
\text{Prob} (S_{2n}=n)=\frac{1}{2^{2n}}{2n\choose n}=\frac{1}{2^{2n}}\frac{(2n)!}{(n!)^2} \sim \frac{1}{\sqrt{\pi n}}\to 0,\ \ (n\to \infty).
\end{equation}

另一方面，由于硬币正反面概率相同，我们期望得到正面的概率几乎是总次数的一半，即对于足够大的$n$,
\begin{equation}
\frac{S_{2n}}{2n}\approx \frac{1}{2}.
\end{equation}
这种说法是正确的，并且体现在大数定律（以后介绍）中。
现在我们简单观察一下尽管当$n\to \infty$时，$S_{2n}=n$的概率趋于$0$，
但是当$n\to \infty$时，$S_{2n}$很靠近$n$的概率趋于$1$.
更精确的说，对于任意的$\epsilon >0$,
\begin{equation}
\text{Prob}\Big{(}\Big{|}\frac{S_{2n}}{2n}-\frac{1}{2}\Big{|}>\epsilon\Big{)}\to 0,\ \ n\to \infty.
\end{equation}
下面来证明这个极限。
注意到分布$S_{2n}=k$在$k=n$处是单峰对称，则对于$\epsilon$足够小且$n\gg 1$有，
\begin{equation}\notag
\begin{aligned}
\text{Prob}\Big{(}\Big{|}\frac{S_{2n}}{2n}-\frac{1}{2}\Big{|}>\epsilon\Big{)}
&\le 2\cdot \frac{1}{2^{2n}}\sum_{k>n+2n\epsilon}\frac{(2n)!}{k!(2n-k)!}\\\
&\le 2(n-2n\epsilon)\cdot \frac{1}{2^{2n}}\frac{(2n)!}{\lceil n+2n\epsilon\rceil !\lfloor n-2n\epsilon\rfloor !}\\\
&\sim \frac{2\sqrt{1-2\epsilon}}{\sqrt{\pi(1+2\epsilon)}}\cdot \frac{\sqrt{n}}{(1-2\epsilon)^{n(1-2\epsilon)}(1+2\epsilon)^{n(1+2\epsilon)}}
\to 0.
\end{aligned}
\end{equation}
其中$\lceil\cdot\rceil$和$\lfloor\cdot\rfloor$分别表示向上取整和向下取整，
即对于$x\in [m,m+1)$($m\in \mathbb{Z}$, ) $\lceil x\rceil=m+1$，和$\lfloor x\rfloor=m$.
这是弱大数定律的一个特例。

对于抛硬币的例子，一次实验中得到结果的数量是有限的。
相对之下，下面将是一个连续集的可能结果。
考虑单位向量$\tau$的方向。
记$\mathbb{S}^2$为$\mathbb{R}^3$上的单位圆。
对于$\boldsymbol{n}\in \mathbb{S}^2$，定义$\rho(\boldsymbol{n}) $为方向分布密度函数，即对于$A\subset \mathbb{S}^2$,
\begin{equation}
\text{Prob}(\tau\in A)=\int _{A}\rho(\boldsymbol{n})dS,
\end{equation}
其中$dS$是$\mathbb{S}^2$上的表面积元。
如果$\tau$没有一个更偏向的方向，即点在任何的方向都是等概率的，则
\begin{equation}
\rho(\boldsymbol{n})=\frac{1}{4\pi}.
\end{equation}
这种情形，称$\tau$是各向同性的。
另一方面，如果$\tau$有偏向的方向$\boldsymbol{n}_0$，
则期望$\rho(\boldsymbol{n})$在$\boldsymbol{n}_0$处是最大值。

## 2.概率空间
正如Kolmogorov做的那样，在这些直观的概率概念上简历坚实的数学基础是必要的。
为了做到这些，首先需要建立概率空间，通常写作$(\Omega,\mathcal{F},\mathbb{P})$,定义如下：

**定义(样本空间)**
所有可能结果组成的集合叫样本空间。
样本空间中每一个元$\omega \in \Omega$叫样本点。

**定义($\sigma $-代数)**
$\sigma $-代数($\sigma $-域)$\mathcal{F}$是$\Omega$上的一个子集族，并且满足如下条件:
- (i) $\Omega \in \mathcal{F}$;
- (ii) 如果$A\in \mathcal{F}$，则$A^{c}\in \mathcal{F}$,其中$A^{c}=\Omega\backslash  A$是$A$在$\Omega$中的补集;
- (iii) 如果$A_1,A_2,\cdots \in \mathcal{F}$, 则$\bigcup_{n=1}^{\infty} A_{n}\in \mathcal{F}$.


$\mathcal{F}$中的每一个集合叫做一个事件。
设$\mathcal{B}$是$\Omega$的一个子集族，
用$\sigma (\mathcal{B})$来表示由集合$\mathcal{B}$生成的最小$\sigma$-代数，
即，包含$\mathcal{B}$的最小$\sigma$-代数。
满足上面性质的$(\Omega, \mathcal{F})$被叫做一个测度空间。

**定义(概率测度)**
概率测度$\mathbb{P}$:$\mathcal{F}\to [0,1]$是定义在$\mathcal{F}$上的一个集合函数,并且满足：
- (a) $\mathbb{P}(\emptyset ) = 0, \mathbb{P}(\Omega)=1$;
- (b) 如果$A_1,A_2,\cdots \in \mathcal{F}$是两两互不相交的，即，
$A_{i}\cap A_{j}=\emptyset$($i \neq j$),则
\begin{equation}
\mathbb{P}\Big{(}\bigcup_{n=1}^{\infty} A_{n}\Big{)}=\sum_{n=1}^{\infty}\mathbb{P}(A_{n})
\end{equation}
上面这个等式被称为可列可加性或者$\sigma$-可加性。


**例(投硬币)**
一次实验结果的概率空间可以如下定义。
样本空间$\Omega =\{H,T\}$,其中$H$和$T$分别表示正面和背面。
$\sigma$-代数是
\begin{equation}
\mathcal{F}=\Omega\text{的所有子集}=\\{ \emptyset,\{H\},\{T\},\Omega \\}.
\end{equation}
且
\begin{equation}
\mathbb{P}(\emptyset)=0,\ \ \mathbb{P}(\{H\})=\mathbb{P}(\{T\})=\frac{1}{2},\ \ \mathbb{P}(\Omega)=1.
\end{equation}
对于$n$次独立的抛投，取$\Omega=\{H,T\}^{n}$，$\mathcal{F}=\Omega \text{的所有子集}$，还有
\begin{equation}
\mathbb{P}(A)=\frac{1}{2^n}|A|,
\end{equation}
其中$|A|$是集合$A$的基数，即元素的个数。

**例($\mathbb{S}^2$的方向分布)**
这种情形，样本空间是$\Omega=\mathbb{S}^2$。
设$\mathcal{B}$是$\mathbb{S}^2$上所有开集组成的集合，
可以由任意开集$B\subset \mathbb{R}^3$和$\mathbb{S}^2$的交集来定义。
则可以取$\sigma$-代数是$\mathcal{F}=\sigma (\mathcal{B})$且
\begin{equation}
\mathbb{P}(U)=\frac{U\text{表面积}}{4\pi}\ \ \text{任意 }U\in\mathcal{F}.
\end{equation}

基于上面的框架，集合论的知识可以运用到概率问题上。
例如，如果$A,B\in \mathcal{F}$，$A$和$B$都发生的概率为$\mathbb{P}(A\cap B)$，
$A$和$B$仅仅一个发生的概率是$\mathbb{P}(A\cup B)$，
$A$发生但是$B$不发生的概率为$\mathbb{P}(A\backslash B)$等等。
容易验证
\begin{equation}
A\subseteq B\Rightarrow \mathbb{P}(A)\le \mathbb{P}(B).
\end{equation}
这是由于$B=A\cup (B\backslash A)$，故$\mathbb{P}(B)=\mathbb{P}(A)+\mathbb{P}({B\backslash A})\ge \mathbb{P}(A).$
同时也有
\begin{equation}
\mathbb{P}(A\cup B)\le \mathbb{P}(A)+\mathbb{P}(B)
\end{equation}
由于$A\cup B=A\cup (B\cap A^{c})$，
有$\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B\cap A^{c})\le \mathbb{P}(A)+\mathbb{P}(B).$
最后这个不等式被称作Boole不等式。

## 3.条件概率
设$A,B\in \mathcal{F}$且$\mathbb{P}(B)\neq 0$。
则在给定$B$的时候，$A$的条件概率定义为
\begin{equation}
\mathbb{P}(A|B)=\frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}.
\end{equation}
上式是给定$B$时$A$和$B$同时发生的概率。
例如，在两次抛投硬币时获得两次正面的概率是$1/4$。
但是给定第一次是正面的情况下，两次都是正面的概率是$1/2$，
而第一次是反面时对应概率是$0$。

由于$\mathbb{P}(A\cap B)=\mathbb{P}(A|B)\mathbb{P}(B)$（由定义可知），有
\begin{equation}
\mathbb{P}(A\cap B\cap C)=\mathbb{P}(A|B \cap C)\mathbb{P}(B|C)\mathbb{P}(C).
\end{equation}
类似可以展开$n$个事件的情形。
从条件概率的定义有
\begin{equation}
\mathbb{P}(A|B)=\frac{\mathbb{P}(A)\mathbb{P}(B|A)}{\mathbb{P}(B)}.
\end{equation}
上式被称为Bayes定律。

**命题(Bayes定理)**
如果$A_1,A_2,\cdots$是互补相交的集合满足$\bigcup_{j=1}^{\infty}=\Omega$，
则有
\begin{equation}
\mathbb{P}(A_j|B)=\frac{\mathbb{P}(A_j)\mathbb{P}(B|A_j)}{\sum_{n=1}^{\infty}\mathbb{P}(A_n)\mathbb{P}(B|A_n)}\ \ \text{任意}j\in \mathbb{N}.
\end{equation}
其中$A_j$对应假设中的事件，$\mathbb{P}(A_j)$是对应假设中$A_j$的先验概率。
这在Bayesian统计中很有用。
概率$\mathbb{P}(A_j|B)$是给定$B$发生时$A_j$的后验概率。

## 4.离散分布
如果$\Omega$的元素有限或者可数，记作$\Omega = \{\omega_1, \omega_2,\cdots\}$，则可有离散概率空间和离散分布的形式。
这种情形，设$X(\omega_j)=x_j$和
\begin{equation}
p_j = \mathbb{P}(X=x_j),\ \ j=0,1,\cdots.
\end{equation}
当然，必须满足
\begin{equation}
0\le p_j \le 1,\ \ \ \sum_{j}p_j=1.
\end{equation}
给定一个关于$X$的函数，如果以下求和良定，它的期望为：
\begin{equation}
\mathbb{E}f(X)=\sum_{j}f(x_j)p_j.
\end{equation}
特别的，分布在时刻$t$的定义为
\begin{equation}
m_{t}=\sum_{j}x_j^{t} p_j
\end{equation}
当$t=1$，上式表示随机变量的均值，也被记作 $\text{mean}(X)$。
另一个重要的变量是方差，定义为
\begin{equation}
\text{Var}(X)=m_2-m_1^2=\sum_{j}(x_j-m_1)^2p_j.
\end{equation}
**例(Bernoulli分布)**
分布的形式如下：
\begin{equation}\notag
\mathbb{P}(X=j)=
\begin{cases}
p,\ \ j=1,\\\
q,\ \ j=0,
\end{cases}
\end{equation}
其中，$p+q=1$且$p,q\ge 0$。
当$p=q=1/2$时，分布与投硬币实验对应。
它的期望和方差直接计算可得：
\begin{equation}
\mathbb{E}X = p,\ \  \text{Var}(X)=pq.
\end{equation}

### 例(二项分布$B(n,p)$)
分布的形式为：
\begin{equation}
\mathbb{P}(X=k)= \binom{n}{k}p^{k}q^{n-k},\ \ \ k=0,1,\cdots,n.
\end{equation}
容易求得：
\begin{equation}
\mathbb{E}X=np,\ \ \  \text{Var}(X)=npq.
\end{equation}

二项分布$B(n,p)$可以通过对$n$个独立的Bernoulli实验求和获得。

**例(Poisson 分布 $\mathcal{P}(\lambda)$)**
分布的形式为，
\begin{equation}
\mathbb{P}(X=k)=\frac{\lambda^k}{k!}e^{-\lambda}, \ \ \ k=0,1,\cdots.
\end{equation}
它的期望和方差分别是：
\begin{equation}
\mathbb{E}X=\text{Var}(X)=\lambda.
\end{equation}
这个分布通常来描述一个时间区间内事件的数量，或者落在给定集合中点的数量。

其实，Poisson分布$\mathcal{P}(\lambda)$也可以看作二项分布在如下意义的极限：
\begin{equation}
C_{n}^{k}p^{k}q^{n-k}\to \frac{\lambda^k}{k!}e^{-\lambda}\ \ (n\to \infty ,p\to 0,np\to \lambda).
\end{equation}
证明留作习题感兴趣的可以证明。

## 5.连续分布
现在考虑$\Omega$不一定可数的一般情形。
从定义随机变量开始，
用$\mathcal{R}$标记$\mathbb{R}$上的Borel $\sigma$-代数，
即包含所有开集的最小$\sigma$-代数。

**定义**
随机变量$X$是一个$\mathcal{F}$-可测的实变量函数$X:\Omega\to \mathbb{R}$，
即任意的$B\in \mathcal{R},\ \ X^{-1}(B)\in \mathcal{F}$。

**定义**
随机变量$X$的分布是$\mathbb{R}$上的一个概率测度$\mu$，对于任意的$B\in \mathcal{R}$定义为
\begin{equation}
\mu(B)=\mathbb{P}(X\in B)=\mathbb{P}\circ X^{-1}(B).
\end{equation}
特别当$B=(-\infty,x]$，定义分布函数为$F(x)=\mathbb{P}(X\le x)$。


对于任意的$B\in \mathcal{R}$，如果存在可积函数$\rho(x)$满足
\begin{equation}
\mu(B)=\int_{B}\rho(x)dx,
\end{equation}
则$\rho$被叫做$X$的概率密度函数(PDF)。
如果$\mu(dx)$关于Lebesgue测度$m(dx)$绝对连续(即对于任意集合$B\in \mathcal{R}$，如果$m(B)=0$，则$\mu(B)=0$)，有$\rho(x)=d\mu/dm$是$\mu(dx)$关于$m(dx)$的Radon-Nikodym导数。
这种情形写作$\mu \ll m$。

**定义**
如果下面的积分是良定的，则随机变量$X$的期望定义为
\begin{equation}
\mathbb{E}X=\int_{\Omega}X(\omega)\mathbb{P}(d\omega)=\int_{\mathbb{R}}x\mu(dx).
\end{equation}
$X$的方差定义为
\begin{equation}
\text{Var}(X)=\mathbb{E}(X-\mathbb{E}X)^2.
\end{equation}
对于两个随机变量$X$和$Y$定义他们的随机系数为
\begin{equation}
\text{Cov}(X,Y)=\mathbb{E}(X-\mathbb{E}X)(Y-\mathbb{E}Y).
\end{equation}
如果$\text{Cov}(X,Y)=0$，$X$和$Y$叫做不相关的。


上面所有的定义可以扩展到向量情形，如$X=(X_1,X_2,\cdots,X_d)^T\in\mathbb{R}^d$是一个随机向量，它的每一个分量$X_k$是一个随机变量。
这种情形，$X$的相关矩阵定义为
\begin{equation}
\text{Cov}(X)=\mathbb{E}(X-\mathbb{E}X)(X-\mathbb{E}X)^{T}.
\end{equation}

**定义**
对于任意的$p\ge 1$，空间$L^{p}(\Omega)$包含第$p$时刻是有限的随机变量：
\begin{equation}
L^{p}(\Omega)=\{X(\omega):\mathbb{E}|X|^{p}<\infty\}.
\end{equation}
对于$X\in L^p(\Omega)$，设
\begin{equation}
\|X\|_{p}=(\mathbb{E}|X|^{p})^{1/p},\ \ p\ge 1.
\end{equation}


**定理**
- (i) Minkowski不等式.

$$
\|X+Y\|_{p}\le \|X\|_{p}+\|Y\|_{p},\ \ p\ge 1,\ X,Y\in L^{p}(\Omega).
$$

- (ii) H\"older不等式.

$$
\mathbb{E}|(X,Y)|\le \|X\|_{p}\|Y\|_{q},\ \ p>1,1/p+1/q=1,X\in L^{p}(\Omega),Y\in L^{q}(\Omega),
$$

其中$(X,Y)$表示$\mathbb{R}^{d}$上的标准标量乘积。
- (iii) Schwartz不等式.

$$
\mathbb{E}|(X,Y)|\le \|X\|_{2}\|Y\|_{2}.
$$

显然Schwartz不等式是H\"older不等式在$p=q=2$的特殊情形。

证明是常见的，这里不重复了。
也能证明$\|\cdot\|_{p}$是一个范数。进一步可以证明$L^{p}(\Omega)$是一个Banach空间和$L^{2}(\Omega)$是一个Hilbert空间对于内积为：

$$
(X,Y)_{L^{2}_{\omega}}=\mathbb{E}(X,Y).
$$

**引理(Chebyshev不等式)**
设$X$是一个随机变量满足对于某个$p$有$\mathbb{E}|X|^{p}<\infty$。则对于任意正数$\lambda$
\begin{equation}
\mathbb{P}\{|X|\ge \lambda\}\le \frac{1}{\lambda^p}\mathbb{E}|X|^p.
\end{equation}

**证明**
对于任意的$\lambda >0$,
\begin{equation}
\mathbb{E}|X|^{p}=\int_{\mathbb{R}^{d}}|x|^{p}\mu(dx)\ge \int_{|x|\ge \lambda}|x|^{p}\mu(dx)\ge \lambda^{p}\int_{|x|\ge \lambda}\mu(dx)=\lambda^{p}\mathbb{P}(|X|\ge \lambda).
\end{equation}
$ \blacksquare $

直接可以将上述估计推广到任何非负递增函数，即如果$f(\lambda)>0$
则$\mathbb{P}(|X|\ge \lambda)\le \mathbb{E}f(|X|)/f(\lambda)$。

**引理(Jensen不等式)**
设$X$是一个随机变量，满足$\mathbb{E}|X|< \infty$且$\phi: \mathbb{R}\to \mathbb{R}$是一个凸函数满足$\mathbb{E}|\phi(X)|<\infty$。则
\begin{equation}
\mathbb{E}\phi(X)\ge \phi(\mathbb{E}X).
\end{equation}

证明可以直接由凸函数的定义得到。下面列出一些经典的连续分布。

**例(均匀分布)**
区域$B$(包含于$\mathbb{R}^d$)上的均匀分布通过如下概率密度分布来定义：
\begin{equation}\notag
\rho(x)=
\begin{cases}
\frac{1}{\text{vol}(B)},\ \ &x\in B,\\\
0,\ \ &x\notin B.
\end{cases}
\end{equation}

在一维时如果$B=[0,1]$(后面记作$\mathcal{U}[0,1]$)，化简为
\begin{equation}\notag
\rho(x)=
\begin{cases}
1,\ \ &x\in [0,1],\\\
0,\ \ &x\notin [0,1].
\end{cases}
\end{equation}
对于$[0,1]$上的均匀分布，有

$$\mathbb{E}X=\frac{1}{2},\ \ \text{Var}(X)=\frac{1}{12}.$$

**例(指数分布)**
指数分布$\mathcal{E}(\lambda)$通过下面的概率密度函数定义：
\begin{equation}\notag
\rho(x)=
\begin{cases}
0,\ \ &x<0\\\
\lambda e^{-\lambda x},\ \ &x\ge 0.
\end{cases}
\end{equation}

$E(\lambda)$的期望和方差是
\begin{equation}
\mathbb{E}X=\frac{1}{\lambda},\ \ \ \text{Var}(X)=\frac{1}{\lambda^2}.
\end{equation}

作为示例，具有速率$\lambda$的Poisson过程的等待时间是参数为$\lambda$的指数分布。

**例(正态分布)**
一维正态分布(也被称为Gaussian分布)$N(\mu,\sigma^2)$通过下面的概率密度函数定义：
\begin{equation}\notag
\rho(x)=\frac{1}{\sqrt{2\pi \sigma^2}}\exp\big{(}-\frac{1}{2\sigma^2}(x-\mu)^2\big{)},
\end{equation}
其中$\mu$是期望值，$\sigma^2$是方差。

如果$\Sigma$是一个$n\times n$的正定对称矩阵和$\mu$是$\mathbb{R}^{n}$上的向量，则可以定义$n$维正态分布$N(\mu,\Sigma)$的密度为
\begin{equation}\notag
\rho(x)=\frac{1}{(2\pi)^{n/2} (\det \Sigma)^{1/2}} \exp\big{(}-\frac{1}{2}(x-\mu)^{T}\Sigma^{-1}(x-\mu)\big{)}.
\end{equation}
可以计算
\begin{equation}
\mathbb{E} X=\mu,\ \ \text{Cov}(X)=\Sigma.
\end{equation}


在生活中，正态分布几乎是最重要的分布。
它也被叫做Gaussian分布。
正态分布的随机变量也被叫做高斯随机变量。
对于退化情形(即，相关矩阵$\Sigma$不可逆，这种情形一些分量属于其他分量张成的子空间)，Gaussian分布需要通过特征函数来定义。

**例(Gibbs分布)**
在平衡统计力学中，我们关心状态空间$S$上的概率分布$\pi$。
对于$n$个粒子系统的连续状态情形，有$x=(x_{1},\cdots,x_{n},p_{1},\cdots,p_{n})\in S=\mathbb{R}^{6n}$，其中$x_{k}$和$p_{k}$分别是第$k$个粒子的位置和动量。
Gibbs分布的概率密度函数$\pi(x)$有如下特殊形式:
\begin{equation}
\pi (x)=\frac{1}{Z}e^{-\beta H(x)},\ \ \ x\in \mathbb{R}^{6n},\beta=(k_{B}T)^{-1},
\end{equation}
其中$H$是系统的能量，$T$是绝对温度，$k_{B}$是Boltzmann常数和分区函数
\begin{equation}
Z=\int_{\mathbb{R}^{6n}}e^{-\beta H(x)}dx.
\end{equation}
如果$f(x)$是定义在配置空间上的函数。则它的热力学平均$\langle f  \rangle$(即$f$得期望)是
\begin{equation}
\mathbb{E}f=\langle f\rangle=\int_{\mathbb{R}^{6n}}f(x)\pi (x)dx.
\end{equation}
利用求和代替积分类似地可以得到离散空间上的定义。


另一个重要的概念是随机变量$X$的分布函数：
\begin{equation}
F(x)=\mathbb{P}(X<x).
\end{equation}
容易发现，如果$X$的分布关于Lebesgue绝对连续，则$X$的密度和分布函数有关系
\begin{equation}
\rho (x)=\frac{\mathrm{d}}{\mathrm{d}x}F(x).
\end{equation}


声明：文章内容是学习文献1的笔记和一些个人看法。个人能力有限难免会有错误和不当，欢迎指正。对于本文表述不清的部分可以参看原书。
## 参考文献
1.Weinan E, Tiejun Li, Eric Vanden-Eijnden. Applied Stochastic Analysis.  American Mathematical Society, 2019.

