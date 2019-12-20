---
layout: post
title:  "MATLAB Essentials 5"
subtitle:   "Matlab具体应用"
header-img: "resources/matlab.png"
date:   2019-12-17 17:30:00 +0800
tags:
    - MATLAB
    - PHYSICS
---

## Index of _Matlab Essentials_
* [Matlab基本语法和数据结构](./MATLAB-Essentials-1.html)
* [Matlab常用绘图函数](./MATLAB-Essentials-2.html)
* [Matlab符号化系统](./MATLAB-Essentials-3.html)
* [Matlab解物理问题的常用算法](./MATLAB-Essentials-4.html)
* [Matlab具体应用](./MATLAB-Essentials-5.html)

## 带电粒子在电荷环作用下的运动

## 特殊函数

## 费根鲍姆图(迭代法)

```matlab
u = 2.6:0.001:4;
X = zeros(250,1401);
X(1,:) = 0.6;
for j = 2:250
    X(j,:) = u.*(X(j-1,:) - X(j-1,:).^2);
end
plot(u,X(120:250,:)', 'r.', 'markersize', 1)
```
![费根鲍姆图](/resources/matlab/fig_5_1.png)

> ***Problem***
> 
> 为何取 `X(1,:) = 0.6` 作初值?

## 分形

### Lindenmayer符号系统

| 符号 | 定义 |
|:-:|:-|
| "`F`" | 按给定长度向前画线段，可以迭代(变量符号) `X` 向前画线段，所画线段不可以迭代(常量符号) |
| "`+`" | 逆时针方向转一个给定的角度(左转) |
| "`-`" | 顺时针方向转一个给定的角度(右转)/反向转180度 |
| "`[`" | 存储当前的位置及角度信息 |
| "`]`" | 回到左方括号 `[` 前的画图状态 |

### 相似移动法

### 复变函数迭代法

