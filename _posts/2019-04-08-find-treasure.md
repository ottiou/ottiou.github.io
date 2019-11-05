---
layout: post
title:  "利用复数寻宝"
date:   2019-04-08 22:27:55 +0800
categories: math
---
# 如何利用复数找到简单宝藏
本文使用“虚”数的方法来求解一个现实世界中的问题：怎么寻找丢失已久的宝藏。 

首先，我们提一个启发，复数（形式为a  +  bi的表达式 ，其中实数  a  和  b  加入虚数单位i，代表平方根-1）在数学中自然地出现与任何其他类型的数字一样。
他们不应该被称为“虚的”。正如负数在可数对象的领域中是不自然的，但在会计领域和作为数字线的原点左边的距离变得非常自然。
所以类似地当我们从一维数字线移动到二维平面时，复数也是完全很自然地产生。

上个月，我们展示了如何在二维平面上的点中分配唯一的复数，即实部和虚部分别表示它们与原点的水平和垂直距离。
与实数一样，这些数字也可以相加或相乘，并且产生另一个复数。
复数上的每个代数运算完全对应了特定的几何操作，这些操作将您带到结果所代表的点。
加法是向量加法，乘法表示绕原点转动，乘以i是顺时针直角转动，乘以-i是逆时针转动。复平面上两点的中点就是它们的平均值。

基于这些复数的基础知识，我们求解二月谜题来找到隐藏的宝藏。

**寻找一号宝藏**
第一次寻宝是著名核物理学家George Gamow 在著作''One, Two, Three … Infinity''中描述的活动的一个变型。
寻宝活动发生在一个有两棵树（橡树和松树）和古老绞刑架的岛屿上。
以下段落是如何根据这三点找到宝藏的关键：

“Start thou from the gallows and walk to the oak counting thy steps. 
At the oak thou must turn right by a right angle and take exactly three times as many steps as thou just took to reach the tree. 
Put here a spike into the ground. 
Now must thou return to the gallows and walk to the pine counting thy steps.
At the pine thou must turn left by a right angle and again take exactly three times as many steps as thou took to reach the tree. Put thou another spike into the ground. Dig halfway between the spikes; the treasure is there.”

翻译：
“开始，数着脚步，从绞刑架走到橡树前。
在橡树处，你必须以一个直角向右转，并且再走刚刚到达橡树前步数的三倍。
在这里放一个钉子。
现在你必须回到绞刑架前，然后数着你的脚步走到松树前。
在松树处，向左转一个直角，然后再走到达松树前三倍的步数。
把另一个钉子放到这儿的地上。
宝藏在两个钉子的正中间。”

不幸的是，现在绞刑架已经消失并且没有任何痕迹。试问我们还能找到宝藏吗？

当然能找到！所要做的就是应用上述在复平面上的运算。
首先建立坐标轴，使橡树处于$-1$，松树处于$+1$。
（注意，这两点的坐标可以自由选择，因为总是可以将这些坐标映射到任意系统，正如数学家所说“不失一般性”。）

按照惯例，假设绞刑架所在的点为$z$，来观察它可以带我们到哪里。
（在他的叙述中，Gamow幽默地使用了希腊字母$gamma(\Gamma)$来达到这个目的，因为“它看起来像一个绞刑架。”
嗯，你可以把z视为现代绞刑架，设计上有更稳定的重心。）
由于在原点周围定义了直角，让我们假装橡树是原点。
相对于橡树，绞架位于$z+1$.
我们需要乘以$i$然后乘以$3$才能找到第一个钉子的位置，
因此在相对于橡树$3i(z+1)= 3iz+3i$位置处。
因为橡树从真正的原点平移了-1，故相对于真正的原点，这一点是$3iz+3i-1$。
类似地，第二个钉子相对于松树位于$3(-i)(z-1)=3i-3iz$，
在真正坐标中为$3 i -3 iz + 1$。
宝藏位于两个钉子的正中点，即$(3 iz + 3 i - 1 + 3 i - 3 iz + 1)/ 2=3i$。
因此，绞刑架的位置与宝藏的位置无关。
偷偷摸摸的海盗！
解题者Douglas Felix说：“你站到橡木与松木一半的地方，前面距离橡木$d$步，后面距离松树$d$步，右转然后步行$3d$步，开始挖！”


所有寻宝者都必须这样做，而不是随意挖掘，想象绞刑架在随机某一点。
正如我们的第一个很有洞察的难题，把“从随机中获得信息”，转化为真实信息可以由寻宝者从随机猜测中“神奇地”获得。
虽然我们失去宝藏的故事对于主角来说是悲惨的，但是对那些确实找到这个宝藏的读者表示祝贺。
MZH超越了它，揭示了诗句中的位置。
聪明！Ahmad Khalifa也很聪明，他使用了smart-aleck推理，只有当绞刑架的位置无关紧要时才可以问这个谜题，所以我们可以把绞刑架放在我们喜欢的任何地方。
为了简单起见，我们可以将它放在原点，橡树位于（-1,0），松树位于（+1,0）。现在我们可以很容易地看到宝藏将在（0,3）。

**寻找二号宝藏**
对于问题二，宝藏的线索来自这首神秘的诗：

An eye for an eye and a tooth for a tooth

Recall thee the pirate creed. Forsooth!

At the lonely oak we rounded traitors, aye!

Then took them to the pine, minus eye.

Dead men’s chests swelled the treasure so big!

Ponder ye the creed: eye to the eye! Now go dig.

Manuel Fortin是唯一按照我的意图破译这首诗的人。以下是关键行（已翻译）：

At the lonely oak we rounded traitors, aye!（橡树在$i$。）

Then took them to the pine, minus eye. （松树在$-i$。）

Ponder ye the creed: eye to the eye! Now go dig.（宝藏在$i^i$。）

那么，如何才能找到$i^i$？为此，我们需要欧拉公式：$e^{i\pi}=-1$，其涉及了数学上三个著名常数：$e,\pi, i$。我们先不考虑这个公式的意义，只是用它来寻找宝藏。

对于欧拉公式，两边开平方有，$e^{i\pi/2}=i$ 。
再在两边取$i$次幂，得到$e^{-\pi/2}=i^i$ 。
可以借助科学计算计算$e^{-\pi/2}$ ，大约是$0.208$。
看起来很奇怪吧，$i^i$是约为$1/5$的实数！

剩下就很容易了。用Manuel Fortin的话来说:
“所以，在坐标系中橡树在$i$，松树在$-i$，宝藏大概在$0.208$左右。
为了得到第二个宝藏，走到两棵树之间，左边是橡树，走到距离中点和任何树木约$1/5$的地方; 就会接近宝藏。
如果你可以非常准确地测量东西，那么距离是$0.208$倍。“