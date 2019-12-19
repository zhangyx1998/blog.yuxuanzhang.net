---
layout: post
title:  "MATLAB Essentials 4"
subtitle:   "Matlab解物理问题的常用算法"
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
* **Matlab解物理问题的常用算法(本文)**
* [Matlab具体应用](./MATLAB-Essentials-5.html)

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
![费根鲍姆图](/resources/matlab/fig_3_1.png)

> ***Problem***
> 
> 为何取 `X(1,:) = 0.6` 作初值?

## 求方程零点的几种方法

## 龙格—库塔法

## 刚性问题

## 初值问题

## `ode`函数集

## `pdetools`

## 边值问题

## 打靶法

## 