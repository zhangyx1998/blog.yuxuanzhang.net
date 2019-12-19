---
layout: post
title:  "MATLAB Essentials 2"
subtitle:   "Matlab常用绘图函数"
header-img: "resources/matlab.png"
date:   2019-12-17 16:30:00 +0800
tags:
    - MATLAB
    - PHYSICS
---

### Index of _Matlab Essentials_
* [Matlab基本语法和数据结构](./MATLAB-Essentials-1.html)
* **Matlab常用绘图函数(本文)**
* [Matlab常用运算函数](./MATLAB-Essentials-3.html)
* [Matlab具体应用](./MATLAB-Essentials-4.html)

### 基本概念

Matlab自带画图的工具是基于窗口(`figure`)和图像(`axes`)的, 在每个窗口(`figure`)中可以建立 `m × n` 个图像(`axes`), 其中相邻的图像可以合并成一个较大的图像, 方便排版.

Matlab绘图窗口和图像的样式都有极大的自定义空间, 几乎可以满足任何类型的使用需求, 在绘制完成后还可以直接以矢量图或者矢量PDF的形式导出, 从而获得高质量的成品图像.

每次在某一个子图像上绘制点/线/面时都可以得到这个对象的句柄(作为返回值), 通过对象句柄可以修改对象属性(比如外观或者节点坐标), 也可以获得对象当前的状态.

### 绘图控制指令及函数

| 指令/函数 | 功能 |
| :-: | :-- |
|`figure`   | 弹出(新建)绘图窗口, 并返回该窗口句柄 |
|`figure(n)`| 新建(或者切换到)编号为 `n` 的绘图窗口, 并返回该窗口句柄 |
|`subplot(m,n,P)`| 将当前窗口分成 `m` 行 × `n` 列, 在第 `P` 区作图, 子图像按照先行后列的方式编号 |
|`subplot(P)`| 在当前窗口的第 `P` 区作图. 需要注意的是 `P` 可以是一个向量, 例如 `P = [1,2]` 将会将第一第二个自图像合并. 同时 `subplot()` 函数会返回当前图像句柄 |
|`clf`      | 清空当前作图区 |
|`hold on`  | 绘制新对象时保留画布上的旧图像 |
|`hold off` | 绘制新对象时清除画布上的旧图像 |
|`hold(AX,'on')`<br>`hold(AX,'off')` | 通过 `axes` 句柄指定 `hold on/off` 的作用对象 |
|`close`<br>`close(gcf)`| 关闭当前绘图窗口 |
|`close(figure(N))`| 关闭编号为 `N` 的绘图窗口 |

### 样式指令

| 指令/函数 | 功能 |
| :-: | :-- |
|`axis equal`   | 令当前图像横纵坐标等比 |
|`axis([x1,x2,y1,y2,z1,z2])`| 设定图像显示范围 |
|`set(handle,'Property',balue)`| 设置特定对象的特定样式 |

### 绘图相关的环境变量

| 变量 | 内容 |
| :-: | :--  |
|`gca`       | _**G**et handle of **c**urrent **a**xis._<br>返回当前**图像**句柄. |
|`gcf`       | _**G**et handle of **c**urrent **f**igure._<br>返回当前**窗口**句柄. |
|`figure(n)` | 新建(或者切换到)编号为 `n` 的绘图窗口, 并返回该窗口句柄. |
|`hold on`   | 绘制新对象时**保留**画布上的旧图像 |
|`hold off`  | 绘制新对象时**清除**画布上的旧图像 |

### (进阶)句柄操作

> 略, 稍后补充

### 二维图像绘制函数

+ `plot()` 
> 
> *最通用的绘图函数, 可以接受一个向量或两个向量作为坐标输入, 但是两个向量作为输入时这两个向量必须有相同的长度* 
> 
> ```matlab
> >> x = -pi:pi/10:pi;                          % 从-pi到pi等间距(步长 pi/10)取点
> >> y = tan(sin(x)) - sin(tan(x));             % 计算函数值
> >> plot(x,y,'-rs','LineWidth',2,...
>                   'MarkerEdgeColor','k',...
>                   'MarkerFaceColor','b',...
>                   'MarkerSize',6)
> ```
> ![Result](/resources/matlab/fig_2_1.png)

+ *ezplot()*
> 
> *快捷绘图指令, 可以大大简化编程过程, 仅需要通过字符串的形式输入待求解表达式(甚至隐函数方程), 即可得到结果* 
> 
> ```matlab
> >> ezplot('x^2+y^2 = 1')
> ```
> ![示例: 通过隐函数方程画图](/resources/matlab/fig_2_2.png)

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