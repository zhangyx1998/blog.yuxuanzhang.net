---
layout: post
title: "概率论主要理论和公式"
subtitle: "Probability Fundamentals"
header-img: "resources/physics.png"
date: 2020-01-01 00:09:00 +0800
tags:
    - Probability
    - MyCourses
mathjax: true
---

## 各种分布的符号标记

+ 二项分布 (泊松分布)
  > $X\sim B(n,p) \Rightarrow P(X = i)=C_n^ip^i(1-p)^{i-1}~,~~~~i\in(1,\dots,n)$
+ 正态分布
  + 一维
    > $X \sim N(\mu,\sigma)$
  + 二维
    > $(X,Y) \sim N(\mu_1,\sigma_1;~\mu_2,\sigma_2;~\rho)$
  + 详见下文
+ 指数分布
  > $X\sim exp(\lambda) \Rightarrow f(x)=\lambda e^{-\lambda x}~,~~~~x\in\mathbb{R}^+$.
+ 均匀分布
  > $X\sim U(a,b)$ 其中 $(a,b)$ 表示均匀分布的范围, 它不可以是无限远.

## 一维和二维正态分布

+ 一维正态分布
  > $$ f(x) = \dfrac{1}{\sqrt{2\pi}\,\sigma}\,e^{-\frac{1}{2}\,\big(\frac{x-\mu}{\sigma}\big)^2} $$
  >
  > 显然, 上式中, $\sigma$ 是 $f(x)$ 的标准差(表现在图像上就是概率峰的展宽), $\mu$ 是概率中心点(极大值点)的位置, 同时也是 $f(x)$ 的数学期望.
  >
  > 若随机变量 $X$ 符合上述分布,可以记作 $X \sim N(\mu,\sigma)$
+ 二维正态分布
  > $$\begin{array}{rcl}
  > f(x,y) &=& \dfrac{1}{2\pi\,\sigma_1\sigma_2\,\sqrt{1-\rho^2}}\,
  > exp\Big[
  >   -\dfrac{1}{2(1-\rho^2)}\,
  >   \Big(
  >       \big(\dfrac{x-\mu_1}{\sigma_1}\big)^2
  >     + \big(\dfrac{y-\mu_2}{\sigma_2}\big)^2
  >     - 2\rho\dfrac{(x-\mu_1)(y-\mu_2)}{\sigma_1\sigma_2}
  >   \Big)
  > \Big]
  > \end{array}$$
  >
  > 与一维的情况不同, 二维正态分布引入了干涉项 $\sigma$. 这一项的取值代表了随机变量 $x,y$ 的相关性.
  >
  > 若随机变量 $X,Y$ 符合上述分布,可以记作 $(X,Y) \sim N(\mu_1,\sigma_1;~\mu_2,\sigma_2;~\rho)$
  >
  > 为了更加直观地体现出干涉项在二维正态分布中的作用, 我们用随机变量空间中的线性变换简化上述表达式.
  >
  > 令 $x' = \dfrac{x-\mu_1}{\sigma_1}, y' = \dfrac{y-\mu_2}{\sigma_2}$ , 研究 $x'=x_0$ 时 $\rho$ 的作用:
  >
  > $$\begin{array}{rcl}
  > f(x,y) &=& \dfrac{1}{2\pi\,\sqrt{1-\rho^2}}\,
  > exp\Big[
  >   -\dfrac{1}{2(1-\rho^2)}\,
  >   \Big(
  >       x'^2
  >     + y'^2
  >     - 2\rho\,x'y'
  >   \Big)
  > \Big]\\
  > f(y)_{x'=x_0} &=& \dfrac{A_0}{2\pi\,\sqrt{1-\rho^2}}\,
  > exp\Big[
  >   -\dfrac{1}{2(1-\rho^2)}\,
  >   \Big(
  >       y'^2
  >     - (2\rho\,x_0)\,y'
  >     + x_0^2
  >   \Big)
  > \Big]\\
  > &=& \dfrac{A_0}{2\pi\,\sqrt{1-\rho^2}}\,
  > exp\Big[
  >   -\dfrac{1}{2(1-\rho^2)}\,
  >   \Big(
  >       y'
  >     - 2\rho\,x_0
  >   \Big)^2
  > \Big]
  > \cdot exp\Big[Const\Big]\\
  > &=& C_0\cdot
  > exp\Big[
  >   -\dfrac{1}{2}\,
  >   \Big(
  >     \dfrac{y' - 2\rho\,x_0}
  >           {\sqrt{1-\rho^2}}
  >   \Big)^2
  > \Big]
  > \end{array}$$
  > 
  > 由上述推导 ($C_0$ 是归一化因子) 可见, 干涉项 $\rho$ 不为零时, 会对 $x'=x_0$ 时的剖面 $f(y)_{x'=x_0}$ 的中心点 (期望) 和展宽 (方差) 同时产生影响, 且两者之间具有定量关系:
  >
  > $$ \sigma_{y,x=x_0} = \sqrt{1-\rho^2} \\ \mu_{y,x=x_0} = 2\rho\,x_0 $$

  ```plain
  Question: 上述对二维正态分布的干涉项的解读是否正确?
  Question: 作上述变换时, 如何证明归一化因子分母上的Sigma可以直接消去?
  Question: 上述两个分布的公式是否需要准确背诵?
  Question: 为何干涉项方差不含 x0?
  Qusetion: 干涉项rho是否可以是 x 和(或) y 的函数?
  ```

## `期望`, `方差` 和 `协方差`

通过定义一些数学量, 我们可以更加直观地刻画随机变量的特征.

+ 数学期望 (***E**xpectation*)
  > 定义:
  >
  > $$ E(X) = \sum\limits_{i} X_ip_i = \int x\,p(x)\,dx $$
  >
  > 性质:
  > 1. $E(C) = C~,~~~~C = Const$
  > 1. $E(CX)=CE(X)$
  > 1. $E(X+Y)=E(X)+E(Y)$
  > 1. 若 $X,Y$ 相互独立, 则: $E(XY)=E(X)E(Y)$
+ 方差 (***D**eviation*)
  > 方差的定义:
  >
  > $$ D(X) = E\Big[\big(X-E(X)\big)^2\Big] = E(X^2) - E(X)^2 $$
  >
  > 上述第二个等号是根据方差的性质推导而来的
  > 
  > 性质:
  > 1. $D(C) = 0~,~~~~C = Const$ 常数的方差为0.
  > 1. $D(CX) = C^2\,D(X)$
  > 1. $D(X\pm Y) = D(X) + D(Y) \pm Cov(X,Y)$
  > 1. $D(X) = 0 \Leftrightarrow X = Const$

  ```plain
  Question: 书P72 定义3.2.1 歧义?
  Question: 如何证明 E(X^2) >= E(X)^2 ?
  ```
+ 标准差 (***St**andard **d**eviation, or **std** for short*)
  > $$ \sigma(X) = \sqrt{E(X)} $$
  >
  > 即方差开根号, 其意义在于保持量纲与 X 相同.
+ 协方差 (***Cov**ariance*)
  > 协方差的定义:
  >
  > $$ Cov(X,Y) = E\Big(\big(X-E(X)\big)\big(Y-E(Y)\big)\Big) $$
  协方差的功能是体现两个随机变量的独立性, 对于完全独立的两个随机变量, 其协方差为零 (但是 $Cov(X,Y)=0$ 不能判定 $X,Y$ 独立).
+ 相关系数 $\rho$
  > $$\rho_{XY} = \dfrac{Cov(X,Y)}{\sqrt{D(X)}\,\sqrt{D(Y)}}$$
  > X 与 Y 独立 $\Rightarrow \rho_{XY} = 0$

  ```plain
  Question: 如何判定X与Y相互独立?
  Question: P75页 柯西-施瓦茨不等式的含义是什么?
  ```
+ 矩
  > 定义:
  > 
  > + 若存在:
  >
  >   $$ \alpha_n = E(X^n) $$
  >
  >   则称 $\alpha_n$ 为 $X$ 的 $n$ 阶***原点矩***.
  > 
  > + 若存在:
  >
  >   $$ \mu_n = E\big[\big(X-E(X)\big)^n\big] $$
  >
  >   则称 $\mu_n$ 为 $X$ 的 $n$ 阶***中心矩***.
  >
  >   数学期望即为二阶中心矩.
  > 
  > + 若存在:
  >
  >   $$ \alpha_{kl} = E(X^kY^l) $$
  >
  >   则称 $\alpha_{kl}$ 为 $X$ 的 $k+l$ 阶***混合原点矩***.
  > 
  > + 若存在:
  >
  >   $$ \mu_{kl} = E\big[\big(X-E(X)\big)^k\big(Y-E(Y)\big)^l\big] $$
  >
  >   则称 $\mu_{kl}$ 为 $X$ 的 $k+l$ 阶***混合中心矩***.
  >
  >   使用***混合中心矩***表示协方差和相关系数:
  >
  >   $$ Cov(X,Y) = \mu_{11}\\ \rho_{XY} = \dfrac{\mu_{11}}{\sqrt{\mu_{20}}\,\sqrt{\mu_{02}}} $$

  ```plain
  Question: 原点矩有何实际含义?
  ```

## 大数定律和中心极限定理
+ 引理: ***Chebyshev***不等式
  > $$ P\Big(|X-E(X)|\geq \varepsilon \Big) \leq \dfrac{D(X)}{\varepsilon^2} $$
  >
  > ***Chebyshev***不等式证明了:
  >
  > <center> 方差 $D(X)$ 表征随机变量在其期望值附近的集中程度 </center>
+ 引理: 伯努利大数定律
  > $$ \lim\limits_{n\rightarrow \infty}P\Big(\Big|\dfrac{\eta_n}{n} - p\Big|\geq \varepsilon\Big) = 0~,~~~
  > \forall\varepsilon\in\mathbb{R}^+
  > $$
  >
  > 伯努利大数定律说明: 在大规模随机试验下, 某一事件发生的统计概率 $\dfrac{\eta_n}{n}$ 无限接近于它的实际概率 $p$
+ 中心极限定理
  > 设 $\eta_n$ 是 $n$ 重伯努利试验中事件A 发生的次数, $p$ 是和事件A在单次试验中发生的概率, 则对任意实数 $x\in\mathbb{R}$ 有
  >
  > $$
  > \lim\limits_{n\rightarrow\infty}P\Big(\dfrac{\eta_n-np}{\sqrt{np(1-p)}}\leq x\Big) 
  > = \int_{-\infty}^x\dfrac{e^{-\frac{t^2}{2}}}{\sqrt{2\pi}}dx
  > $$

## 数理统计

+ $\chi^2$ 分布与 $\Gamma$ 函数 _(P103)_
+ $t$ 分布
+ $F$ 分布

  ```plain
  Question: 是否考察?如何考察?
  ```
## 参数估计

+ 参数估计的一般方法
  + 矩阵估计法
  + 极大似然估计法
+ 估计量的评选标准
  + 无偏性
    > 估计参数的期望值与统计量的期望值应该尽量接近.
  + 有效性
    > 估计参数的方差与统计量应该尽量接近.
  + 相合性
    > 估计参数的误差随样本数的增加而减小, 并趋于0.
+ 区间估计
  + 

## 假设检验

+ 建立一对待检验的假设
+ 确定拒绝域
+ 两类错误