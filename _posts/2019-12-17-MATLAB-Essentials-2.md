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

## Index of _Matlab Essentials_
* [Matlab基本语法和数据结构](./MATLAB-Essentials-1.html)
* **Matlab常用绘图函数(本文)**
* [Matlab符号化系统](./MATLAB-Essentials-3.html)
* [Matlab解物理问题的常用算法](./MATLAB-Essentials-4.html)
* [Matlab具体应用](./MATLAB-Essentials-5.html)

## 基本概念

Matlab自带画图的工具是基于窗口(`figure`)和 _图像_ (`axes`)的, 在每个窗口(`figure`)中可以建立 `m × n` 个 _图像_ (`axes`), 其中相邻的 _图像_ 可以合并成一个较大的 _图像_ , 方便排版.

Matlab绘图窗口和 _图像_ 的样式都有极大的自定义空间, 几乎可以满足任何类型的使用需求, 在绘制完成后还可以直接以矢量图或者矢量PDF的形式导出, 从而获得高质量的成品 _图像_ .

每次在某一个子 _图像_ 上绘制点/线/面时都可以得到这个对象的句柄(作为返回值), 通过对象句柄可以修改对象属性(比如外观或者节点坐标), 也可以获得对象当前的状态.

## 绘图控制指令及函数

| 指令/函数 | 功能 |
| :-: | :-- |
|`figure`   | 弹出(新建)绘图窗口, 并返回该窗口句柄 |
|`figure(n)`| 新建(或者切换到)编号为 `n` 的绘图窗口, 并返回该窗口句柄 |
|`subplot(m,n,P)`| 将当前窗口分成 `m` 行 × `n` 列, 在第 `P` 区作图, 子 _图像_ 按照先行后列的方式编号 |
|`subplot(P)`| 在当前窗口的第 `P` 区作图. 需要注意的是 `P` 可以是一个向量, 例如 `P = [1,2]` 将会将第一第二个自 _图像_ 合并. 同时 `subplot()` 函数会返回当前 _图像_ 句柄 |
|`clf`      | 清空当前 窗口 |
|`cla`      | 清空当前 _图像_ |
|`hold on`  | 绘制新对象时保留画布上的旧 _图像_  |
|`hold off` | 绘制新对象时清除画布上的旧 _图像_  |
|`hold(AX,'on')`<br>`hold(AX,'off')` | 通过 `axes` 句柄指定 `hold on/off` 的作用对象 |
|`delete(axes)`| 删除句柄为 `axes` 的图形对象 |
|`close`<br>`close(gcf)`| 关闭当前绘图窗口 |
|`close(figure(N))`| 关闭编号为 `N` 的绘图窗口 |

## 样式指令

| 指令/函数 | 功能 |
| :-: | :-- |
|`axis equal`   | 令当前 _图像_ 横纵坐标等比 |
|`axis([x1,x2,y1,y2,z1,z2])`| 设定 _图像_ 显示范围 |
|`set(handle,'Property',balue)`| 设置特定对象的特定样式 |

## 绘图相关的环境变量

| 变量 | 内容 |
| :-: | :--  |
|`gca`       | _**G**et handle of **c**urrent **a**xis._<br>返回当前**_图像_**句柄. |
|`gcf`       | _**G**et handle of **c**urrent **f**igure._<br>返回当前**窗口**句柄. |
|`figure(n)` | 新建(或者切换到)编号为 `n` 的绘图窗口, 并返回该窗口句柄. |
|`hold on`   | 绘制新对象时**保留**画布上的旧 _图像_  |
|`hold off`  | 绘制新对象时**清除**画布上的旧 _图像_  |

## (进阶)句柄操作

> 略, 稍后补充

## 二维 _图像_ 绘制

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

+ `ezplot()`
> 
> *快捷绘图指令, 可以大大简化编程过程, 仅需要通过字符串的形式输入待求解表达式(甚至隐函数方程), 即可得到结果* 
> 
> ```matlab
> >> ezplot('x^2+y^2 = 1')
> ```
> ![示例: 通过隐函数方程画图](/resources/matlab/fig_2_2.png)

## 三维 _图像_ 绘制

| 函数 | 功能 |
| :-: | :--  |
｜`mesh()`   | 绘制网线图           ｜
｜`meshz()`  | 绘制网线图再加基准平面 ｜
｜`surfc()`  | 绘制表面图再加光照    ｜
｜`meshc()`  | 绘制网线图再加等高线   ｜
｜`surf()`   | 绘制表面图           ｜

> 示例: 几种不同的三维画图指令应用
> ```matlab
> subplot(2, 2, 1);
> z = 0:0.01:15;
> x = sin(z);
> y = cos(z);
> plot3(x, y, z, '-.');
> view(-60, 18);
> title("plot3()");
> 
> subplot(2, 2, 2);
> sphere(40);
> title("sphere()");
> 
> subplot(2, 2, 3);
> R =sqrt(X.^2 + Y.^2) + eps;
> [X,Y]=meshgrid(-8:0.5:8);
> Z = sin(R)./R;
> surf(X, Y, Z);
> title("surf()");
> ```
> ![示例: 三种不同的三维画图指令应用](/resources/matlab/fig_2_3.png)

> 示例: 同一函数在不同画法下的外观
> ```matlab
> R =sqrt(X.^2 + Y.^2) + eps;
> [X,Y] = meshgrid(-8:0.5:8);
> Z = sin(R)./R;
> 
> subplot(2, 2, 1);
> mesh(X, Y, Z);
> title("mesh( )");
> 
> subplot(2, 2, 2);
> meshz(X, Y, Z);
> title("meshz( )");
> 
> subplot(2, 2, 3);
> meshc(X, Y, Z);
> title("meshc( )");
> 
> subplot(2, 2, 4);
> surfc(X, Y, Z);
> title("surfc( )");
> ```
> ![示例: 同一函数在不同画法下的外观](/resources/matlab/fig_2_4.png)

## 应用: 绘制两曲面相交区域

> ```matlab
> hold on;
> grid on;
> [x,y]=meshgrid(-2:0.01:2);
> z1 = x.^2 - 2*y.^2;
> z2 = 2*x - 3*y;
> mesh(x,y,z1);
> mesh(x,y,z2);
> cr  = abs(z1 - z2) < 0.01;
> avg = (z1+z2)./2;
> plot3(x(cr), y(cr), avg(cr),'*k');
> ```
> ![应用: 绘制两曲面相交区域](/resources/matlab/fig_2_5.png)'

## 物理场可视化

主要手段:
* 等高线(等势面/等势线)
* 流线图

### 

## 进阶: 使用 `colormap()` 函数自定义 _图像_ 色彩

略, 稍后补充

## 附: 使用 `help` 命令熟悉函数功能

在 Matlab 命令界面中输入 `help` 即可获得对某个函数的描述, 包含所有可能的引用方法, 甚至可以提供联想建议.

实际上, Matlab `help` 命令足以解决绝大多数问题, 熟练使用 `help` 命令可以大大减少上网搜索浪费的时间.

```matlab
>> help colormap
 colormap Color look-up table.
    colormap(MAP) sets the current figure's colormap to MAP.
    colormap('default') sets the current figure's colormap to
    the root's default, whose setting is PARULA.
    MAP = colormap returns the three-column matrix of RGB triplets defining 
    the colormap for the current figure.
    colormap(FIG,...) sets the colormap for the figure specified by FIG.
    colormap(AX,...) sets the colormap for the axes specified by AX. 
    Each axes within a figure can have a unique colormap. After you set
    an axes colormap, changing the figure colormap does not affect the axes.
    MAP = colormap(FIG) returns the colormap for the figure specified by FIG.
    MAP = colormap(AX) returns the colormap for the axes specified by AX.
 
    A color map matrix may have any number of rows, but it must have
    exactly 3 columns.  Each row is interpreted as a color, with the
    first element specifying the intensity of red light, the second
    green, and the third blue.  Color intensity can be specified on the
    interval 0.0 to 1.0.
    For example, [0 0 0] is black, [1 1 1] is white,
    [1 0 0] is pure red, [.5 .5 .5] is gray, and
    [127/255 1 212/255] is aquamarine.
 
    Graphics objects that use pseudocolor  -- SURFACE and PATCH objects,
    which are created by the functions MESH, SURF, and PCOLOR -- map
    a color matrix, C, whose values are in the range [Cmin, Cmax],
    to an array of indices, k, in the range [1, m].
    The values of Cmin and Cmax are either min(min(C)) and max(max(C)),
    or are specified by CAXIS.  The mapping is linear, with Cmin
    mapping to index 1 and Cmax mapping to index m.  The indices are
    then used with the colormap to determine the color associated
    with each matrix element.  See CAXIS for details.
 
    Type HELP GRAPH3D to see a number of useful colormaps.
 
    colormap is a function that sets the Colormap property of a figure.
 
    See also hsv, caxis, spinmap, brighten, rgbplot, figure, colormapeditor.
```