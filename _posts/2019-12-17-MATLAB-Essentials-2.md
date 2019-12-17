---
layout: post
title:  "MATLAB Essentials 2"
subtitle:   "常用函数"
header-img: "resources/matlab.png"
date:   2019-12-17 16:30:00 +0800
tags:
    - MATLAB
    - PHYSICS
---

### Index of _Matlab Essentials_
* [基本语法和数据结构](./MATLAB-Essentials-1.html)
* **Matlab常用函数(本文)**
* [具体应用](./MATLAB-Essentials-3.html)

### linspace()

### 使用 help 命令熟悉函数功能

在 Matlab 命令界面中输入 `help` 即可获得对某个函数的描述, 包含所有可能用到的引用方法.

```matlab
>> help linspace
 linspace Linearly spaced vector.
    linspace(X1, X2) generates a row vector of 100 linearly
    equally spaced points between X1 and X2.
 
    linspace(X1, X2, N) generates N points between X1 and X2.
    For N = 1, linspace returns X2.
 
    Class support for inputs X1,X2:
       float: double, single
```