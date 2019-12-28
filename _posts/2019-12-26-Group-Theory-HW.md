---
layout: post
title: "群论作业汇总"
subtitle: "王延申老师授课"
header-img: "resources/physics.png"
date: 2019-12-26 00:12:00 +0800
tags:
    - GroupTheory
    - Physics
    - MyCourses
mathjax: true
---

<span id="1.12"></span>

#### [`1.12`](#1.12) 证明除恒等元外的所有元都是二阶的群是阿贝尔群.
> `证明:`
> 
> 若:
> 
> $$\forall A_n \in G ,~A_n \neq E ,~A_n^2 = E$$
> 
> 且由群的封闭性可知:
> 
> $$\forall A_j,\,A_k \in G,\,A_j\,A_k \in G$$
> 
> 即 $A_j\,A_k$ 也满足\,$\left(A_j\,A_k\right)^2 = E$
> 
> 所以:
> 
> $$\begin{align*}
>     A_j\,A_k    &= A_j\,\cdot\,E\cdot\,A_k\\
>                 &= A_j\,\left(A_j\,A_k\,A_j\,A_k\right)\,A_k\\
>                 &= \left(A_j\,A_j\right)\,A_k\,A_j\,\left(A_k\,A_k\right)\\
>                 &= A_k\,A_j
> \end{align*}$$
> 
> 即 $A_j\,A_k = A_k\,A_j~(j\neq k)$ 对群$G$内的所有群元成立.
> 
> `原命题得证`

<span id="1.14"></span>

#### [`1.14`](#1.14) 证明每个(所有)指数为2的子群是正规子群.
> `证明:`
>
> 设群 $G$ 及其子群 $S$ 满足 $g = 2s$, 并设 $X\,\in\,G$ ,则:
> 
> 1. 若$X\,\in\,S$, 则显然:
> 
>   $$ XS\,=\,SX\,=\,S $$
>
> 2. 若$X\,\notin\,S$,则:
> 
>   $$\forall S_i \in S,\,XS_i\,\notin\,S,\,XS_i\,\in\,G$$
> 
>   $$\forall S_i,\,S_j \in S\,(i\neq j),\,XS_i\,\neq\,XS_j$$
> 
> + 相似地:
> 
>   $$\forall S_i \in S,\,S_iX\,\notin\,S,\,S_iX\,\in\,G$$
> 
>   $$\forall S_i,\,S_j \in S\,(i\neq j),\,S_iX\,\neq\,S_jX$$
> 
> 即:
> 
> 集合 $XS,\,SX$ 均含有 $s$ 个各不相同, 且不属于 $S$ , 但属于 $G$的元,
> 
> 又因为 $G$ 中不属于 $S$ 的元的数量与 $S$ 的元数量相等(均为 $s$ 个),所以:
> 
> $$ XS\,=\,SX\,=\,G-S $$
> 
> 综合(1)(2)两种情况: 
> 
> $$~\forall X\,\in\,G,\,XS\,=\,SX~$$
> 
> `原命题得证`

<span id="1.15"></span>

#### [`1.15`](#1.15) 若 $G = H \otimes K$ 证明:

1. **商群 $ G / H $ 与 $ K $ 同构**
> `证明:`
>
> 直积群可以展开为:
> 
> $$\begin{align*}
>     G = H \otimes K
>         &= \sum\limits\limits_{i,j}^{} H_j K_i\\
>         &= \sum\limits\limits_{i}^{} H\cdot K_i
> \end{align*}$$
> 
> 由商群的定义可知:
> 
> $$ G/H\,=\,\{HA_1,HA_2,...,HA_k\} $$
> 
> 其中, $k$ 是群 $K$ 的阶, $A_1$ 是群 $H,K,G$ 的共同单位元 $E$.
> 
> 不失一般性,假设 $A_n = H_j K_i\,(n\neq 1)$:
> 
> $$\begin{align*}
>     H A_n
>         &= H H_j K_i \\
>         &= (H H_j) K_i \\
>         &= H K_i
> \end{align*}$$
> 
> 即:  $\{A_2,...,A_k\}$ 与 $\{K_2,...,K_k\}$ 一一对应
> 
> 比较直积群的展开和商群的定义,加上上述对应关系,可以得出:
> 
> $$ G/H\,=\,\{HK_1,HK_2,...,HK_k\} $$
> 
> 构造同构对应关系:
> 
> $$ HK_n \leftrightarrow K_n $$
> 
> 利用直积的对易关系($K_i H = H K_i$),验证同构性质:
> 
> $$\begin{align*}
>     (H K_i) (H K_j) = H^2 K_i K_j &= H (K_i K_j) \\
>     K_i K_j &= (K_i K_j) 
> \end{align*}$$
> 
> 所以,原命题得证.

2. **$G$ 与 $H$ 及 $K$ 同态**
> `证明:`
>
> 对于 $G$ 与 $H$, 构造同态关系:
> 
> $$ H_i K_j \rightarrow H_i\,(1\leq i\leq h,\,1\leq j\leq k)$$
> 
> 利用直积的对易关系,验证同态性质:
> 
> $$\begin{align*}
>     (H_i K_n) (H_j K_n) &= (H_i H_j) K_n^2 \\
>     H_i H_j &= (H_i H_j)
> \end{align*}$$
> 
> 由于 $K_n^2 = K_{n'} \in K$, 所以映射 $(H_i H_j) K_n^2 \rightarrow (H_i H_j)$ 依然成立.
> 
> $G$ 与 $K$ 的同态映射构造及证明与上述过程完全一致,不再赘述.
> 
> `原命题得证`

<span id="1.18"></span>

#### [`1.18`](#1.18) 证明二阶循环群与四阶循环群同态.
> `证明:`
>
> 不失一般性,令
> 
> $$\begin{align*}
>     A&=\{E,\alpha\}&(E=\alpha^2)\\
>     B&=\{E,\beta,\beta^2,\beta^3\}&(E=\beta^4)
> \end{align*}$$
> 
> 则可以构造映射关系:
> 
> $$\begin{align*}
>     B_1,\,B_3 \rightarrow A_1\\
>     B_2,\,B_4 \rightarrow A_2
> \end{align*}$$
> 
> 验证同态性质:
> 
> $$\begin{align*}
>     \left.\begin{array}{rl}
>         B_1\,B_1 &= B_1\\
>         B_1\,B_3 &= B_3\\
>         B_3\,B_1 &= B_3\\
>         B_3\,B_3 &= B_1
>     \end{array}\right\}
>     \rightarrow A_1A_1 = A_1 &~~~~&
>     \left.\begin{array}{rl}
>         B_1\,B_2 &= B_2\\
>         B_1\,B_4 &= B_4\\
>         B_3\,B_2 &= B_4\\
>         B_3\,B_4 &= B_2
>     \end{array}\right\}
>     \rightarrow A_1A_2 = A_2\\
>     \left.\begin{array}{rl}
>         B_2\,B_1 &= B_2\\
>         B_2\,B_3 &= B_2\\
>         B_4\,B_1 &= B_4\\
>         B_4\,B_3 &= B_4
>     \end{array}\right\}
>     \rightarrow A_2A_1 = A_2 &~~~~&
>     \left.\begin{array}{rl}
>         B_2\,B_2 &= B_1\\
>         B_2\,B_4 &= B_1\\
>         B_4\,B_2 &= B_3\\
>         B_4\,B_4 &= B_3
>     \end{array}\right\}
>     \rightarrow A_2A_2 = A_1
> \end{align*}$$
> 
> `原命题得证`

<span id="1.19"></span>

#### [`1.19`](#1.19) 在有限群中有一组元的集合 $S$, 对于群乘是封闭的, 试证明集合 $S$ 中必包含单位元及各元的逆元.
> `证明:`
> 
> 用 $S = \{S_1,S_2,...,S_s\}$ 表示群 $S$.
> 
> 已知: $\forall S_n,S_m\in S,\,\,S_n S_m = S_k\in S$.
> 
> 且由于S是一有限群的子集,所以S的群元依然满足结合律,并且S中的群元各不相同.
> 
> **1. 首先证明单位元存在.**
> 
>    由群乘的封闭性, $\exists S_k \in S$, 使得:
>       
>    $$ S_1\cdot S_2\cdot...\cdot S_s = S_k $$
>    
>    即:
>  
>    $$ (S_1\cdot S_2\cdot...\cdot S_{k-1}\cdot S_{k+1}\cdot...\cdot S_s) >     S_k = S_k $$
>    
>    再次利用群乘的封闭性, 可知 $\exists S_t \in S,\, (S_t\neq S_k)$, 使得:
>  
>    $$S_t = (S_1\cdot S_2\cdot...\cdot S_{k-1}\cdot S_{k+1}\cdot...\cdot > S_s)$$
>    
>    故上式简化为:
>  
>    $$ S_m\cdot S_k = S_k $$
>    
>    所以:
>  
>    $$ S_m = E~~or~~S_k = E $$
>    
>    上述步骤完成了群 $S$ 中存在单位元的证明.
> 
> **2. 接下来证明S中包含各元的逆元.**
> 
>    不失一般性, 我们设 $S_1 = E$.
>    
>    再次利用群乘的封闭性, $\exists S_k \in S$, 使得:
>  
>    $$ S_2\cdot S_3\cdot...\cdot S_s = S_k $$
>    
>    1. 如果 $S_k = E$,那么由于 $S$ 中群元各不相同,可知 $\forall S_t \in S,\, > (S_t\neq S_k)$, 使得:
>  
>    $$S_t\cdot(S_2\cdot S_2\cdot...\cdot S_{t-1}\cdot S_{t+1}> \cdot...\cdot S_s) = E$$
>  
>    $$S_1\cdot S_2\cdot...\cdot S_{t-1}\cdot S_{t+1}\cdot...\cdot S_s= > S_t^{-1} \neq S_t$$
>    
>    2. 如果 $S_k \neq E$,那么:
>  
>    $$S_k\cdot(S_2\cdot S_2\cdot...\cdot S_{k-1}\cdot S_{k+1}> \cdot...\cdot S_s) = E$$
>  
>    $$S_1\cdot S_2\cdot...\cdot S_{k-1}\cdot S_{k+1}\cdot...\cdot S_s= > S_k^{-1} \neq S_k$$
>    
>    将 $S_k$ 从上述连乘序列中剔除, 我们就得到第一种情况,从而证明了任意的群元都有对应的> 逆元.\\
> 
> `综上,原命题得证`

<span id="2.2"></span>

#### [`2.2`](#2.2) 试证明群 $G$ 中属于同一类的各元的表示矩阵之和, 必与群 $G$ 的一切表示矩阵对易.
> `证明:`
> 
> 设群
> $$G = \{X_1,X_2,\dots,X_k,\dots,X_g\}$$
> 含有类
> $$C = \{C_1,C_2,...C_n\}$$
> 
> 其中 $X_k$ 是任意群元, 满足:
> 
> $$X^{-1}_kCX_k = C$$
> 
> 即:
> 
> $$D(X^{-1}_kCX_k) = D(C)$$
> 
> 所以:
> 
> $$\begin{array}{rcl}
>     \Big(\sum\limits_{i=1}^{n}D(C_i)\Big)D(X_k)
>     &=&\sum\limits_{i=1}^{n}
>         D(X_kC_iX^{-1}_k)~D(X_k)\\
>     &=&\sum\limits_{i=1}^{n}
>         D(X_k)~D(C_i)~D(X^{-1}_k)~D(X_k)\\
>     &=&\sum\limits_{i=1}^{n}
>         D(X_k)~D(C_i)~D(X^{-1}_kX_k)\\
>     &=&\sum\limits_{i=1}^{n}
>         D(X_k)~D(C_i)\\
>     &=&D(X_k)\sum\limits_{i=1}^{n}
>         D(C_i)\\
> \end{array}$$
> 
> `证毕`

<span id="2.10"></span>

#### [`2.10`](#2.10) 一个群的两个不等价的不可约表示可以有完全相同的特征标吗?
> `解:`
> 
> **不能**， 证明如下
> 
> 由 `表示的正交性定理`
> 
> $$ \sum\limits_{R\in G} D^i(R)^*_{\alpha\gamma}\,D^j(R)_{\beta\delta}
>    = \delta_{ij}\delta_{\alpha\beta}\delta_{\gamma\delta}\frac{g}{l_j} $$
> 
> 可以构造出两个表示的特征标的内积表达式:
> 
> 取对角元,即 $\alpha=\gamma, \,\beta=\delta$
> 
> $$
> \sum\limits_{R\in G} D^i(R)^*_{\alpha\alpha}\,D^j(R)_{\beta\beta}
> =
> \delta_{ij}\delta_{\alpha\beta}\dfrac{g}{l_j}
> $$
> 
> 将上式对 $\alpha$ 求和, 并调整求和运算顺序
> 
> $$
> \sum\limits_{\alpha}\Big(\sum\limits_{R\in G} D^i(R)^*_{\alpha\alpha}\,D^j(R)_{\beta\beta}\Big)
> =
> \sum\limits_{\alpha}\delta_{ij}\delta_{\alpha\beta}\dfrac{g}{l_j}
> \\
> \sum\limits_{R\in G}\Big(\sum\limits_{\alpha} D^i(R)^*_{\alpha\alpha}\Big)\,D^j(R)_{\beta\beta}
> =
> \delta_{ij}\Big(\sum\limits_{\alpha}\delta_{\alpha\beta}\Big)\dfrac{g}{l_j}
> \\
> \sum\limits_{R\in G}\chi^i(R)^*\,D^j(R)_{\beta\beta} =
> \delta_{ij}\dfrac{g}{l_j}$$
> 
> 再对 $\beta$ 求和
> 
> $$
> \sum\limits_{R\in G}\Big(\chi^i(R)^*\,\sum\limits_{\beta}D^j(R)_{\beta\beta}\Big) =
> \sum\limits_{\beta}\delta_{ij}\dfrac{g}{l_j}
> $$
> 
> 注意到 $\beta$ 共有 $l_j$ 个不同取值
> 
> $$
> \sum\limits_{R\in G}\chi^i(R)^*\,\chi^j(R)\, =
> \delta_{ij}\,g$$
> 
> 如果 $\chi^i(R)$ 和 $\chi^j(R)$ 完全相同, 那么其内积一定大于零 (考虑到类 $E$ 的存在), 即上式中 $i=j$.
> 
> 但是 $i=j$ 即两种表示等价, 与原命题冲突, 所以两者特征标不允许完全相同
> 
> `证毕`

```plain
QUESTION:
是否可以通过E类的存在证明内积大于零?
```

<span id="2.13"></span>

#### [`2.13`](#2.13) 用正交法求出三角形对称群 $D_3$ 的特征标表
> `解:`
> 
> 已知 $D_3$ 群有3个类, 所以
> 
> $$ l_1^2 + l_2^2 + l_3^2 = 6 \\ [l_1,~l_2,~l_3] = [1,~1,~2]$$
> 
> 可以部分地写出特征标表:
> 
> $$ \begin{array}{c|c|cc|ccc}
>    & E & D & F & A & B & C\\\hline
> D^1& 1 & 1 & 1 & 1 & 1 & 1\\
> D^2& 1 & a & a & b & b & b\\
> D^3& 2 & c & c & d & d & d
> \end{array}$$
> 
> 再通过正交性定理和完全性关系的约束条件:
> 
> $$\left\{\begin{array}{rcl}
> (D^1,D^2)=& 1+2a+3b   &= 0\\
> (D^1,D^3)=& 2+2c+3d   &= 0\\
> (D^2,D^3)=& 2+2ac+3bd &= 0
> \end{array}\right.
> ~~~~\Rightarrow~~~~
> \left\{\begin{array}{l}
> a=1\\
> b=-1\\
> c=-1\\
> d=0
> \end{array}\right.$$
> 
> 可以唯一地确定第二行和第三行的特征标:
> 
> $$ \begin{array}{c|c|cc|ccc}
>    & E & D & F & A & B & C\\\hline
> D^1& 1 & 1 & 1 & 1 & 1 & 1\\
> D^2& 1 & 1 & 1 &-1 &-1 &-1\\
> D^3& 2 &-1 &-1 & 0 & 0 & 0
> \end{array}$$

<span id="2.14"></span>

#### [`2.14`](#2.14) 试证明下列等式对一切群成立:

$$\sum\limits_{j=1}^r l_j \chi_{(C)}^j = \left\{\begin{matrix}g&,~when&C=E\\0&,~when&C\neq E\end{matrix}\right.$$

> `证明:`
> 
> 从*特征标的完全性关系*出发:
> 
> $$
> \sum\limits_{i=1}^r \chi^i(C_l)^*\,\chi^i(C_m) = \delta_{lm}\dfrac{g}{h_l}
> $$
> 
> 令 $C_l=E$, 则上述等式化为:
> 
> $$
> \sum\limits_{i=1}^r\,l_i\chi^i(C_m) = \delta_{lm}g
> $$
> 
> 其中, $\delta_{lm} = 1$的条件为 $\chi^i(C_l)=\chi^i(C_m)=E$, 
> 显然与题设的分类条件等价
> 
> `等式成立得证`

$$\sum\limits_{C} h_C \chi_{(C)}^j = \left\{\begin{matrix}g&,~when&j=1\\0&,~when&j\neq 1\end{matrix}\right.$$

> `证明:`
> 
> 从*特征标的正交性关系*出发:
> 
> $$
> \sum\limits_C h_C\chi^i(C)^*\,\chi^j(C) = \delta_{ij}g
> $$
> 
> 令 $\chi^i(C)=E$, 则上述等式化为:
> 
> $$
> \sum\limits_{C} h_C \chi_{(C)}^j =  = \delta_{ij}g
> $$
> 
> 其中, $\delta_{ig} = 1$的条件为 $\chi^i=\chi^j=E$, 
> 显然与题设的分类条件等价
> 
> `等式成立得证`

<span id="2.20"></span>

#### [`2.20`](#2.20) 若 $D^i$ 及 $D^j$ 是群 $G$ 的两个不等价的不可约表示, 试证:
1. 直积表示 $D^i\otimes D^{j*}$ 并不包含恒等表示
    > `证明:`
    > 
    > `原命题得证`

2. 一个不可约表示与其复共轭表示的直积中, 恒等表示出现且仅出现一次.
    > `证明:`
    > 
    > `原命题得证`

<span id="4.6"></span>

#### [`4.6`](#4.6) 写出晶体点群 $C_{2h}$ 及 $D_2$ 的乘法表及其类.

<span id="4.8"></span>

#### [`4.8`](#4.8) 找出点群 $C_{3V}$ 的不可约表示矩阵及每一个不可约表示的基函数.

<span id="4.10"></span>

#### [`4.10`](#4.10) 已知点群 $T$ 的三维表示的基函数是 $x,\,y$ 以及 $z$ . 试构造 $T$ 群的三维表示的表示矩阵.

<span id="4.11"></span>

#### [`4.11`](#4.11) 证明点群 $D_n$ 是由 $a$ 及 $b$ 两个元生成的, 生成关系是 $a^n=b^n=(ab)^2=E$ , $E$ 是单位元.

<span id="4.14"></span>

#### [`4.14`](#4.14) 试证明六角晶系的晶体的电容率张量的形式为 

$$
\left[\begin{matrix}
\varepsilon_{\parallel}&0&0\\
0&\varepsilon_{\perp}&0\\
0&0&\varepsilon_{\perp}\\
\end{matrix}\right]
$$

<center>
其中 $\varepsilon_{\parallel}$ 及 $\varepsilon_{\perp}$ 分别为平行及垂直于六度轴的分量.
</center>

<span id="3.1"></span>

#### [`3.1`](#3.1) 试证明: 若有 $$X'_i=\sum\limits_j R_{ij}x_j$$, 则有 $$\dfrac{\partial}{\partial x'_i}=\sum\limits_j R_{ij}\dfrac{\partial}{\partial x_j}$$.

<span id="3.2"></span>

#### [`3.2`](#3.2) 利用式 `3.1-39` 分别算出绕 $x,y,z$ 轴转动 $\phi$ 角的转动矩阵.

<span id="3.5"></span>

#### [`3.5`](#3.5) 试以 $l=1$ 的球鞋函数为基函数, 求出完全转动群的不可约表示 $D^1(\alpha,\beta,\gamma)$ .

<span id="3.7"></span>

#### [`3.7`](#3.7) $l=$ *整数* 时, 证明 $D^1(0,0,\gamma)$ 是对角矩阵.

***

1.1

1.2

1.15

1.11