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
<span id="2.2"></span>
### 2.2 试证明群 $G$ 中属于同一类的各元的表示矩阵之和, 必与群 $G$ 的一切表示矩阵对易.
    
证明:

设群
$$G = \{X_1,X_2,\dots,X_k,\dots,X_g\}$$
含有类
$$C = \{C_1,C_2,...C_n\}$$

其中 $X_k$ 是任意群元, 满足 

$$X^{-1}_kCX_k = C$$

即

$$D(X^{-1}_kCX_k) = D(C)$$

所以

$$\begin{array}{rcl}
    \sum_{i=1}^{n}D(C_i)~D(X_k)
    &=&\sum_{i=1}^{n}
        D(X_kC_iX^{-1}_k)~D(X_k)\\
    &=&\sum_{i=1}^{n}
        D(X_k)~D(C_i)~D(X^{-1}_k)~D(X_k)\\
    &=&\sum_{i=1}^{n}
        D(X_k)~D(C_i)~D(X^{-1}_kX_k)\\
    &=&\sum_{i=1}^{n}
        D(X_k)~D(C_i)\\
\end{array}$$

证毕

### 2.10 一个群的两个不等价的不可约表示能有完全相同的特征标吗?

