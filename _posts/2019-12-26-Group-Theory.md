---
layout: post
title: "群论课程概要"
subtitle: "王延申老师授课"
header-img: "resources/physics.png"
date: 2019-12-26 00:09:00 +0800
tags:
    - GroupTheory
    - Physics
    - MyCourses
mathjax: true
---

`本文正在编辑, 当前显示内容为草稿`

## 一、 群的基本概念

1. **群**
    <span id="群的定义"></span>
    + ***群的定义***
    > 对于定义了 `内积` (或称 `群乘` ) 的元素的集合 $G = \\{A,B,C,\dots\\}$ , 如果满足以下条件, 则可以称之为 `群` .
    >
    > 1. **封闭性**  
    >
    >     $$\forall A,B\in G,~AB\in G$$
    >
    > 2. **结合律**
    >
    >     $$A(BC)=(AB)C$$
    >
    > 3. **有单位元**
    >
    >     $$\exists E\in G,~\forall A\in G$$
    >
    >     $$EA=AE=A$$  
    >
    > 4. **每个元素存在逆元**
    >
    >     $$\forall A\in G,~\exists A^{-1}\in G$$
    >
    >     $$AA^{-1}=A^{-1}A=E$$

    <span id="阿贝尔群"></span>
    + ***交换群 ( 阿贝尔群 )***
    > 如果群的内积定义满足群内任意两个元素内积等于它们交换位置后的内积:
    >
    > $$\forall A,B\in G$$
    >
    > $$AB=BA$$
    >
    > 那么这个群就称为交换群 ( 或阿贝尔群 ).

    + ***群表***
    >  一种直观地展示群的方法, 下图展示了 $D_3$ 群的群表.
    >
    > <span id="群表"></span>
    >
    > ![群表](/resources/grouptheory/SVG/GroupChart.svg)

    + **常用群 - D<sub>3</sub>群 (等价于C<sub>3v</sub>群)**
    >
    > $$\begin{array}{c|cccccc}
    >   & E & A & B & C & D & F\\\hline
    > E & E & A & B & C & D & F\\
    > A & A & E & D & F & B & C\\
    > B & B & F & E & D & C & A\\
    > C & C & D & F & E & A & B\\
    > D & D & C & A & B & F & E\\
    > F & F & B & C & A & E & D\\
    > \end{array}$$
    >
    > <center>D<sub>3</sub>群的群表</center>
    >
    > 可以将D<sub>3</sub>群理解为对一个三角形的绕对称轴翻转(ABC)和绕中心点旋转(DF)操作构成的群.
    > 
    > 如果将三角形的三个顶点编号为
    >
    > $$\left(\begin{array}{ccc}
    > 1&2&3
    > \end{array}\right)$$
    > 
    > 约定用括号内第一行表示变换前的状态, 第二行表示变换后的状态, 那么, 上述操作对应的变换可以是(不唯一):
    >
    > $$
    > E = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 1 & 2 & 3
    > \end{array}\right)~~~~
    > D = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 3 & 1 & 2
    > \end{array}\right)~~~~
    > F = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 2 & 3 & 1
    > \end{array}\right)\\\,\\
    > A = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 1 & 3 & 2
    > \end{array}\right)~~~~
    > B = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 3 & 2 & 1
    > \end{array}\right)~~~~
    > C = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 2 & 1 & 3
    > \end{array}\right)
    > $$
    > 
    > 如果连续进行两次变换, 比如先进行A变换再进行B变换, 可以写成(注意顺序, 最右边的变换最先进行):
    >
    > $$
    > BA = \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 3 & 2 & 1
    > \end{array}\right)
    > \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 1 & 3 & 2
    > \end{array}\right)
    > =
    > \left(\begin{array}{c}
    > 1 & 2 & 3\\
    > 2 & 3 & 1
    > \end{array}\right)
    > = F
    > $$
    >
    > 通过上式我们顺便验证了群表表示和变换表示结果的一致性.
    >
    > 注意到: D<sub>3</sub>群除E外的所有操作均**不**对易, 因此D<sub>3</sub>群是一个[`非阿贝尔群`](#阿贝尔群)

    + **常用群 - C<sub>4v</sub>群** (对正方形的对称操作群)
    >
    > 定义操作如下:
    >
    > | 变换          | 描述 | 置换表示 |
    > | :-: | :- | :-: |
    > | $$E             $$ | 恒等操作 | ( `1 2 3 4` ) |
    > | $$c_{2z}        $$ | 绕 z 轴旋转 180度 | ( `3 4 1 2` ) |
    > | $$c_{4z}        $$ | 绕 z 轴旋转 90度 | ( `4 1 2 3` ) |
    > | $$c_{4z}^{-1}   $$ | 绕 z 轴旋转 -90度 | ( `2 3 4 1` ) |
    > | $$c_{2x}        $$ | 绕 x 轴翻转 | ( `2 1 4 3` ) |
    > | $$c_{2y}        $$ | 绕 y 轴翻转 | ( `4 3 2 1` ) |
    > | $$Ic_{2xy}      $$ | 绕 x=y 翻转后反演 | ( `1 4 3 2` ) |
    > | $$Ic_{2x\bar{y}}$$ | 绕 x=-y 翻转后反演 | ( `3 2 1 4` ) |
    > 
    > 可以证明, 上述操作的集合构成群.

    ```plain
    QUESTION: 为什么要翻转再反演? C4v群和D2d群是否等价? (Problem 1.7)
    ```

    <span id="循环群"></span>

    + 循环群
    > 如果一个群的所有群元都可以用群中某一个元的幂生成, 那么就称这种群为 `n阶循环群`.
    > 
    > 显然:
    > 1. 表示纯旋转操作的对称群一定是循环群.
    > 2. 循环群一定是[`阿贝尔群`](#阿贝尔群).
    > 3. 阶小于4的群一定是循环群

    + 置换群
    > 如果一个群的置换表示覆盖了置换表示中所有可能出现的排列, 那么这个群就称为 `n阶置换群`, 或 `Pn群`.
    > 
    > P<sub>n</sub>群的阶为 $g=n!$
    > 
    > 例如:
    > + D<sub>3</sub>群（ C<sub>3v</sub>群 ）是 P<sub>3</sub>群
    > + C<sub>4v</sub>群是 P<sub>4</sub>群的**指数为3的子群**


    ```plain
    QUESTION: 3阶及以上的置换群是否一定是非阿贝尔群?
    ```

    <span id="重排列定理"></span>
    + ***重排列定理***
    > 从上述群表可以直观地看出, 对一个群左乘或右乘这个群的任一元, 得到的集合与原群相等, 仅是集合内元素的排列顺序发生了变化(也可能不变).
    > 
    > 另一方面, 群表中每一行(列)的群元排列顺序一定**各不相同**.
    > 
    > 上述定理可以从群的定义出发进行严格证明, 利用重排定理可以帮助推导群表.

    + ***群的阶 $g$***
    > 指群 $G$ 中元的个数

    <span id="群元的阶"></span>
    + ***群元的阶 $\alpha$***
    > 设正整数 $\alpha$, 则对于 $A\in G$, 令 $A^\alpha=E$ 的 $\alpha$ 的最小值称为 **群元 $A$ 的阶**.
    > 
    > 注意:
    > 1. 同一个群中不同群元的阶可以不同.
    > 1. 可以存在无限不循环的 $A^\alpha$.
    > 1. 另外注意群的阶是指群中元素的个数, 需要与这个概念区分.

    + ***群的生成元***
    > 如果群 $G$ 内一部分元的乘积可以组合出这个群的所有元素, 则不失完备性, 可以用这些元表示这个群.
    >
    > 在通过生成元展开群时, 可以通过是否满足 [`重排列定理`](#重排列定理) 来检验是否生成完毕.
    > 
    > 群的生成元的选择**不唯一**, 可以选择多种生成元组合来表示某一个群, 但是一旦给定了生成元, 那么它展开所得到的群是**唯一**的.

2. **子群和陪集**

    + ***子群***
    > 对于一个群内部的一部分元素, 如果这部分元素组成的集合 ( 在原群内积定义下 ) 仍然满足[`群的定义`](#群的定义 "封闭性/结合律/有单位元/每个元素存在逆元"), 则这部分元素构成的集合称为原群的子群.
    >
    + **子群的性质**
    <span id="子群阶定理"></span>
    > `子群阶定理`
    >
    > 设 $g,~s$ 分别是群 $G$ 和它的一个子群 $S$ 的阶, 那么 $g$ 一定是 $s$ 的整数倍.
    >
    > 这个性质可以通过[`子群陪集的性质`](#子群陪集的性质)的相关条目证明.
    > 
    > 推论:
    > 1. 阶为素数的群一定没有子群
    > 2. 阶为素数的群一定是[`循环群`](#循环群)
    
    + ***子群的陪集***
    > 设 $S = \\{E,S_2,S_3,\dots\\}$ 是群 $G$ 的子群, 则对于群 $G$ 中任意不属于 $S$ 的元素 $X$:
    >
    > $XS$ 称为子群 $S$ 关于 $X$ 的 `左陪集`
    >
    > $SX$ 称为子群 $S$ 关于 $X$ 的 `右陪集`
    >
    > <span id="子群陪集的性质"></span>
    > 性质: ( 证明略 )
    > 1. 陪集**一定不是**群
    > 1. 陪集**一定是** $G$ 的子集
    > 1. 陪集中的元素**各不相同**
    > 1. $SX,~SY$ 要么没有相同元, 要么完全相同
    > 1. 如果 $Y\in SX$, 那么 $SY = SX$
    > <span id="子群的指数"></span>
    > 1. 子群一共有 $i-1~~\big(i=g/s,~i\in N\big)$ 个**不同的**陪集, $i$ 是子群的指数.

3. **共轭元与类**<span id="共轭元与类"></span>
    
    对于群 $G$ 中的元素 $A,\,B$ 若存在 $X\in G$ , 令 $B\,=\,X^{-1}AX$ , 则 $A,\,B$ 互为 `共轭元`. (即 $A$ 与 $B$ 共轭).
    > 对于矩阵构成的群(或者群的矩阵表示), 两个元素共轭即相应的两个矩阵相似.

    进一步地, 对于群 $G$ 中具有共轭关系的**所有元素对**构成的集合, 称为群 $G$ 的一个 `类`.
    > `类` 的生成:
    >
    >取 $\forall A\in G$, 令 $C_A = G^{-1}AG$, 对集合 $C_A$ 去重之后得到的集合就是由 $A$ 生成的 $G$ 的一个类.
    
    类的性质:
    1. 单位元自成一类
    2. 一个元素不可能同属于两个不同的类
    3. 除单位元构成的类, 其它任何类都不构成群, 因为不含单位元 $E$
    4. [`阿贝尔群(交换群)`](#阿贝尔群)每个元素自成一类
    5. 对于矩阵群(或[`群的矩阵表示`](#群的矩阵表示)), 同一类中的各元互为相似矩阵, 即有相同的迹 (`Trace`).
    6. 同类元素具有相同的 [`阶`](#群元的阶)

    ```plain
    QUESTION1: 具有相同的阶的元素是否一定同属一类?
    QUESTION2: 同类元素是否一定不对易/不同类元素是否一定对易?
    QUESTION3: 同态映射与群元的类是否存在联系?
    ```

4. **正规子群**

    *在定义 `正规子群` 之前, 需要先铺垫 `共轭子群` 的定义.*
    
    <span id="共轭子群"></span>
    1. **共轭子群**
        > 选取 $G$ 的子群 $S$ 和元素 $X$, 则可以证明 $X^{-1}SX \subset G$, 且 $X^{-1}SX$ 构成群, 称之为 $G$ 的 `共轭子群`.

        ```plain
        QUESTION:
        当 X 属于 S 时, 生成的共轭子群是否一定是 S 自身?
        当 X 不属于 S 时, 生成的共轭子群的群元除 E 外是否与 S 各不相同?
        ```

    *接下来就可以进行 `正规子群` 的定义.*
    
    <span id="正规子群"></span>

    1. **正规子群 (不变子群)**
        > 接上文定义, 如果子群 $S$ 满足:
        >   $$\forall X\in G$$
        >   $$X^{-1}SX = S$$
        > 那么就可以称 $S$ 为 $G$ 的 `正规子群`.
        >
        > 注意: $X^{-1}SX$ 和 $S$ 的排列顺序可以不同.

    2. **正规子群的性质**
        1. 正规子群 $S$ 是由 $G$ 中一个或多个完整的[`类`](#共轭元与类)构成的. 一个或多个完整的[`类`](#共轭元与类)构成的子群 (注意需要构成群) 一定是 $G$ 的正规子群.
        2. $\forall X\in G, SA = AS$, 这条性质同时也是 $S$ 构成正规子群的充要条件.

5. **商群**
   
   受[`子群阶定理`](#子群阶定理)的启发, 我们发现, 若视群 $G$ 的[`正规子群`](#正规子群) $S$ 为一个群元, 可以通过群乘法按照一定的规则将其展开为 $G$ 本身, 我们将这种基于 $S$ 展开 $G$ 的群称作 $G$ 对于 $S$ 的商群, 记作 $G/S$.

   $$G/S=\{S,SA_2,SA_3,\dots,SA_i\}$$

   注意上述展开式中的 $i$ 是[`子群的指数`](#子群的指数), $\\{A_1,\dots,A_i\\}$ 分别是 $S$ 的 $i-1$ 个各不相同的陪集中的任意元.

6. **同构和同态**

    1. **同构**
        > 如果群 $G,~G'$ 中的元素存在某种 **一一对应** 的映射关系, 使得群 $G'$ 的[`群表`](#群表) 经过映射后与 $G$ 等价, 则称两群`同构`.
    2. **同态**
        > 与同构类似, 但是允许 $G\rightarrow G'$ 的映射是 **多对一** 的. 
        >
        > ( 即允许 $g>g'$ )
        >
        > 注意, 同态的定义只要求 $G\rightarrow G'$ 方向的映射, 对 $G\leftarrow G'$ 方向的映射**不作要求**.


        ```plain
        QUESTION: 是否存在两个互相没有包含关系的群 G'1 G'2 , 同时与 G 构成态关系?
        ```

        *上述问题与[`另一个问题`](#Q_Link1)相关*

    3. **同态核**
        > 若 $G,~G'$ 同态, 则与 $G'$ 的单位元 $E'$ 存在映射关系的所有 $G$ 的元构成的集合称为它们的 `同态核` .
        >
        > 显然, 任何群都与 $\\{E\\}$ 同态.

7. **直积群**<span id="直积"></span>

    对于群 $G_a$ 和 $G_b$ , 如果满足

    1. $G_a$ 和 $G_b$ 有且仅有 $E$ 一个群元相同
    2. 两群中所有元素两两对易

    则可以定义直积运算

    $$G_a\otimes G_b = \{E,A_i,\dots,B_j,\dots,A_iB_j,\dots,A_aB_b\}$$

    $$A_i\in G_a,~B_j\in G_b$$

    容易证明:
    1. $G_a\otimes G_b = G_b\otimes G_a$
    2. 直积运算生成的群阶为 $g' = g_a\times g_b$
    3. 若 $G = G_a \otimes G_b$, 则 $G_a$ 和 $G_b$ 是 $G$ 的[`正规子群`](#正规子群)

    > 上述定义可以等价的理解为: 两组完全线性独立 (对易) 的线性变换的集合, 可以张成一个更高自由度的变换的集合, 其中包含两种变换叠加所产生的所有可能结果.

    直积群的[`类`](#共轭元与类):

    > 可以证明, 直积群的类可以由 $G_a,~G_b$ 各自的一个类相乘得到, 并且注意到单位元 $E$ 自成一类, 所以 $G_a$ 和 $G_b$ 包含的类一定是 $G$ 中的类.
    >
    > 另外, (符合预期地), $G$ 中类的个数等于 $G_a$ 和 $G_b$ 中类的个数的乘积, $G$ 中每一个类的群元数等于组成该类的 $G_a$ 和 $G_b$ 中的两个类各自的群元数的乘积.

    **半直积群**

    > 如果群 $G_a,~G_b$ 满足 $G_a$ 在 $G_b$ 的任意群元的相似变换下不变, 即
    > 
    > $$ B_iG_aB_i^{-1} = G_a $$
    > 
    > 那么 $G_a$ 与 $G_b$ 可以构成 `半直积群`, 记作
    >
    > $$G_a\wedge G_b = \{E,A_i,\dots,B_j,\dots,A_iB_j,\dots,A_aB_b\}$$
    >
    > $$A_i\in G_a,~B_j\in G_b$$
    > 
    > 注意半直积运算的两个群的顺序不可以随意对调
    >
    > 当 $G_a\wedge G_b = G_d\wedge G_a$ 时, 这两个群的半直积等价于其直积.
    >
    > 需要注意区分半直积和直积的适用条件:
    >
    > + 直积运算需要 $G_a$ 的任意元与 $G_b$ 的任意元对易, 条件更强
    > + 半直积运算只需要 $G_b$ 的任意元对 $G_a$ 相似变换保持不变, 不要求保持相似变换后 $G_a$ 的顺序.

## 二、 群表示理论

1. **群的矩阵表示**<span id="群的矩阵表示"></span>
   
    + 矩阵表示的定义
        > 与给定群 $G$ **同态** 的**方矩阵**构成的群 $D$ 称为群 $G$ 的 `矩阵表示`.
        > 
        > 如果将 $G\rightarrow D$ 的映射记作 $D(A),~~A\in G$, 则可以得到:
        > 
        > $$D(A)\,D(B)=D(AB)$$
        > 
        > 如果 $G$ 的 `矩阵表示` $D$ 与 $G$ **同构**, 则称 $D$ 是 $G$ 的 `确实表示`.
        > 
        > 将 $D$ 内矩阵行(列)数 $l$ 称为这个 `矩阵表示` 的 `维数`.
        > 
        > 简单性质:
        > 1. $D(E)=I_0$, 其中 $I_0$ 是 $l\times l$ 的**单位矩阵**.
        > 2. $D(A^{-1}) = \\left[D(A)\\right]^{-1}$, 即逆元的矩阵表示等于这个元的矩阵表示的逆.

    <span id="等价表示"></span><span id="相似变换"></span>
    + 等价表示
        > 对于 $l$ 维方矩阵 $M$ 和 $S,~det(S)\neq 0$, $M$ 在 $S$ 下的 `相似变换` 记作
        > 
        > $$M' = S^{-1}MS$$
        > 
        > 则可以定义两个由 `相似变换` 联系起来的矩阵表示是 `等价表示`, 记作 $D_G\sim D'_G$
        > 
        > 由于等价表示的群表完全一致 (同构), 所以默认一切等价的表示为同一种表示.

    <span id="幺正表示"></span><span id="幺正矩阵"></span>
    + 幺正表示
        >  如果一个矩阵 $U$ 的逆矩阵 $U^{-1}$ 等于这个矩阵的**复共轭转置矩阵** $\widetilde{U}^*$, $U$ 就称作 `幺正矩阵` .
        > 
        > 复共轭专制矩阵可以记作 $U^\dagger$, 因此 `幺正矩阵` 的定义可以简化为:
        > 
        > $$U^{-1} = U^\dagger$$
        > 
        > 对任意实正交矩阵 $R$ (即满足 $A\,A^T=E$ 的矩阵), 它一定是幺正矩阵.
        > 
        > 如果一个群的矩阵表示中所有矩阵元都是 `幺正矩阵` , 那么称这个表示为这个群的 `幺正表示` .

    + 幺正表示相关定理:
        > 1. 有限群的任何**非奇异**矩阵表示都可以通过 `相似变换` 化为 `幺正表示` .
        > 2. 如果一个群有两个幺正的 `等价表示` , 那么一定**存在**一个 `幺正矩阵` $U$ 将两个表示通过相似变换联系起来.
        > 
        > 以上两条定理的证明需要熟悉, 参见 `群论及其在固体物理中的应用` *P32*.
        > 
        > 由于可以证明任何群的非奇异矩阵表示都可以等价为一个 `幺正表示` , 所以在讨论群的表示时, **可以默认讨论的是 `幺正表示`**.


        ```plain
        QUSTION:
        同一个群是否存在两个或以上的 不可约 不等价 的 确实的 的 幺正表示?
        ```
    
    <span id="可约表示"></span><span id="不可约表示"></span><span id="直和"></span>
    + 可约表示
        > 设想同一个群 $G$ 的两个等价的矩阵表示 $D^1(A)$ 和 $D^2(A)$, 我们可以构造出一个新的矩阵表示:
        > 
        > $$ D(A) = \left[\begin{array}{cc}D^1(A)&0\\0&D^2(A)\\\end{array}\right]$$
        > 
        > 并证明其与 $D^1(A)$ 和 $D^2(A)$ 同态:
        > 
        > $$ D(A)D(B) = \left[\begin{array}{cc}D^1(A)D^1(B)&0\\0&D^2(A)D^2(B)\\\end{array}\right] = D(AB)$$
        > 
        > 我们将上形式的接矩阵称为 `块状对角矩阵`, 将上述拼接操作称为矩阵表示 $D(G_a)$ 与 $D(G_b)$ 的 `直和`, 记作: 
        >
        > $$D(G_a) \oplus D(G_b)$$ 
        >
        >> 注意区分 [`直积`](#直积) 与 `直和` 的区别. (运算结果的阶/是否产生新的类)
        > 
        > 综上可知, 对于一个矩阵表示, 如果它的每一个矩阵元都可以被块状对角化成**相同结构**, 这种表示称为 `可约表示` , 反之即为 `不可约表示` .
        >
        > ***
        >
        > `有疑问`
        >
        > 需要注意的是, `可约表示` 有可能是由两个 `不确实表示` 作 `直和` 而来的, 所以 `可约表示` 不一定可以化简成更低维的 `确实表示`, 但是一定可以拆分出多个 `不确实表示`.
        > 
        > 只有块状对角化拆分出来的某一个表示与另一个表示 `同构` 时, 才能安全地移除这个部分.
        > 
        > <span id="Q_Link1"></span>
        
        ```plain
        QUESTION1: 同一个群的各种不同不可约表示的矩阵的维数是不是一定相等(最简)?
        QUESTION2: 上述有疑问的STATEMENT是否正确?
        ```
    
2. **舒尔引理**

    > **若有一非零矩阵 $A$ 同一个群的某一表示中的所有矩阵对易**
    > 1. 若此表示是不可约表示, 则 $A$ 只可能是单位矩阵 $E$ 或单位矩阵的常数倍
    > 2. 若 $A$ 不是单位矩阵的常数倍, 则这个群的表示一定可约, 当 $A$ 是厄米矩阵时, 约化矩阵就是使 $A$ 对角化的矩阵

    舒尔引理的逆定理:
    
    > 1. 如果除单位矩阵的常数倍以外, 没有任何非零矩阵能与群 $G$ 的某一表示的所有矩阵对易, 则这个表示是不可约的.
    > 2. 若群 $G$ 的表示是可约的, 那么, 必然存在至少一个非零的、不是单位矩阵的常数被的矩阵与所有表示矩阵对易.

    通过舒尔引理判断一个表示可约:

    > 由于 [`群G中属于同一类的各元的表示矩阵之和, 必与群G的一切表示矩阵对易`](./Group-Theory-HW.html#2.2), 我们可以轻易构造出一个与群 $G$ 的表示中一切矩阵对易的矩阵, 如果我们可以选择一个类, 使得这个矩阵不是零矩阵或 $E$ 的常数倍, 就可以判断这个表示是可约表示.
    >
    > 注意: 这个办法不能确定表示不可约.

3. **表示矩阵元的正交性定理**

    **设 $D_G^i$ 和 $D_G^j$ 是群 $G$ 的两个不等价的不可约的幺正表示, 则**

    $$\sum\limits_{R\in G}
    D^i(R)_{\alpha\gamma}^*
    D^j(R)_{\beta\eta}
    = \delta_{ij}\delta_{\alpha\beta}\delta_{\gamma\eta}\frac{g}{l_j}$$

4. **表示的构造**

    我们已经知道, 对于一个特定的群, 总是可以找到与其具有同构/同态关系的表示矩阵, 那么现在的问题就是如何寻找这样具有同构或者同态关系的矩阵表示.

   1. 对称变换
   2. 函数的变换
   
        ```plain
        QUESTION: [2.4-6] 如何证明函数变换算符 P(R) 是幺正算符?
        ```
   3. 群表示的确立

        ```plain
        QUESTION: 选取基函数的原则和方法是什么? 是否需要保证完备性? 如何验证线性独立?
        ADDON: P47 例2.2 例题中所选基函数是否一定可以化简?
        ```

5. **基函数的性质**

    + `定理一`

        ```plain
        QUESTION: P50 2.5-1式难以理解.
        ```

    + `定理二`
    + `定理三`
    + `定理四`
    + `定理五`

6. **表示的特征标**
    + **特征标的正交性关系**
        > $$
        > \sum\limits_C h_C\chi^i(C)^*\,\chi^j(C) = \delta_{ij}g
        > $$
7. **投影算符**
8. **群元空间**
9.  **正规表示**
    1. **群元空间的算符**
    2. **正规表示**
    3. **不可约表示的维数定理**<span id="不可约表示的维数定理"></span>
        > 一个群的全部不可约表示的维数的平方和等于群 $G$ 的阶 $g$ , 即:
        > 
        > $$ \sum\limits_{i=1}^r l_i^2 = g $$
        >
        > 在处理具体的群时, 许多情况下上述等式只能求出一组解, 因此使用此定理就可以方便地定出每个不可约表示的维数
10. **完全性关系**
    1. **`表示矢量` 的完全性关系**
    2. **不可约表示矩阵元的完全性关系**
    3. **特征标的完全性关系**
        > $$
        > \sum\limits_{i=1}^r \chi^i(C_l)^*\,\chi^i(C_m) = \delta_{lm}\dfrac{g}{h_l}
        > $$
    4. **重要结论**
        > 一个有限群的 `不等价不可约表示` 的总数 $r$ 与群中 `类` 的数目 $c$ 相等
        > 
        > 即每个 `类` 对应一套 `不等价不可约表示`
11. **特征标表的构造**
    1. **正交法**

        前提:
        > 1. 正交性定理
        >     $$\sum\limits_{R\in G}\chi^i(R)^*\,\chi^j(R)\, =\delta_{ij}\,g $$ 
        > 2. 完全性关系
        >     $$\sum\limits_{i=1}^r\chi^i(C_l)^*\,\chi^j(C_m)\, =\delta_{lm}\,\dfrac{g}{h_l} $$ 

        构造:
        > 1. 基于 [`不可约表示的维数定理`](#不可约表示的维数定理) 解出每个不等价不可约表示的维数.
        > 
        > 
        > 
        > 
        > 
        > 

    2. **类和法**

12. **表示的直积**
13. **直积群的表示**
14. **实表示**

## 三、完全转动群 

1. **三维空间中的正交群**
    1. **三维转动矩阵**
    1. **正当转动**
    1. **非正当转动**
    1. **三维空间中的正交群**
1. **完全转动群 $SO(3)$ 的不可约表示**
1. **二维幺模幺正群 $SU(2)$**
1. **$SU(2)$ 群的不可约表示**
1. **双群**

## 四、点群及其应用

1. **点群**
1. **晶体点群的对称操作及对称元素**
1. **晶体点群**
    1. **$32$ 个晶体点群**
    1. **$32$ 个点群的符号及所属晶系**
1. **点群的特征标表**
1. **双点群**
1. **晶体的宏观性质与晶体的对称性**
   1. **张量**
2. **分子的振动谱及简正模**
    1. **分子振动的一般理论**
    2. **力矩阵的块状对角化**
    3. **振动谱及简正模的对称性分析**