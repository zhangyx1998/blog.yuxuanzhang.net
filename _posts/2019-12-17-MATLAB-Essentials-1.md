---
layout: post
title:  "MATLAB Essentials 1"
subtitle:   "Matlab基本语法和数据结构"
header-img: "resources/matlab.png"
date:   2019-12-17 15:30:00 +0800
tags:
    - MATLAB
    - PHYSICS
---

## Index of _Matlab Essentials_
* **Matlab基本语法和数据结构(本文)**
* [Matlab常用绘图函数](./MATLAB-Essentials-2.html)
* [Matlab解物理问题的常用算法](./MATLAB-Essentials-3.html)
* [Matlab具体应用](./MATLAB-Essentials-4.html)

## Matlab矩阵变量

与 Javascript 类似, Matlab 变量使用前不需要声明, 第一次向变量赋值的同时变量就被创建. Matlab 编程中用到的的绝大部分变量是矩阵变量, 如果定义了一维常数变量 `a = 1` , 则等同于定义了1*1的矩阵变量 `a = [1]` .

Matlab中, 用方括号对 `[ ]` 描述矩阵, 矩阵中同一行的元素用逗号 `,` 或者空格分隔, 行与行之间用分号 `;` 分隔.

声明一个行矩阵: 
```matlab
>> a = [1,2,3,4,5]
a =
     1     2     3     4     5
```

声明一个列矩阵:
```matlab
>> a = [1,2,3,4,5]'
a =
     1
     2
     3
     4
     5
```

将一个矩阵做转置:
```matlab
>> a = a'
a =
     1     2     3     4     5
```

需要注意的是, 对于复矩阵 `A` , `A'` 为取共轭运算, `A.'` 为转置操作.

## Matlab eps

## Matlab复数运算

Matlab 的矩阵变量允许复数, 也具有完备的复数运算能力. Matlab 中复数的写法是标准的 `x+yi` 形式. 

需要注意的是, 变量 `i` 默认初始化为复单位 `0.0000 + 1.0000i` , 但由于 `i` 的本质是一个变量, 所以如果 `i` 在运行中被意外赋值, 使用 `x+y*i` 定义复变量将会得到错误的结果.

相比之下, `x+yi` (注意不含 `*` )在任何情况下都能得到正确的结果, 因此在给复数赋值时, 应当注意使用标准的(不含 `*` )的写法.

Matlab 中自带的主要复数运算函数如下:

| 函数 | 功能 |
| :-: | :--- |
|`abs()`| 取模 |
|`real()`| 取实部 |
|`img()`| 取虚部(返回实数) |

另外, 共轭运算( `'` )和转置运算 ( `,'` )的区别已经在[上文](#Matlab矩阵变量)提及

## Cell Array (元阵列)

略, 稍后补充

## Matlab 基本运算符

变量之间的运算符主要有 `+ - * / .* ./ .^` 其中 `.* ./ .^` 为点乘点除、按元素求幂, 正常写法的乘除为矩阵运算.

当加减法运算的对象行列数一致时,正常运算. 当两个矩阵不同大小时,Matlab会尝试将其中一个拓展来满足运算需要:
```matlab
>> a = [1,2]; b = [4,5];
>> a + b
ans =
     5     7

>> a - b
ans =
    -3    -3

>> a + b'
ans =
     5     6
     6     7
```

矩阵乘法和点乘(自动拓展):
```matlab
>> a * b'
ans =
    14

>> a' * b
ans =
     4     5
     8    10

>> a .* b
ans =
     4    10

>> a' .* b
ans =
     4     5
     8    10
```

需要注意的是, Matlab的矩阵运算中左除和右除的区别. 对于矩阵变量 `A` 和 `B` , 有:
```matlab
A \ B = inv(A) * B
A / B = A * inv(B)
```
其中 `inv()` 是矩阵求逆运算.

## 初始化矩阵的几种命令

* `zeros/ones` 以 0/1 初始化指定大小的矩阵
     ```matlab
     >> zeros(2,2)
     ans =
          0     0
          0     0

     >> ones(2,2)
     ans =
          1     1
          1     1
     ```

* `eye(n)` 建立 n*n 的单位矩阵
* `rand(m,n)` 生成 m*n 的随机数矩阵
* `magic(n)` 建立 n*n 的幻方阵
* `randnn(m,n)` 生成m*n 的正态分布的随机数矩阵
* `cell(m,n)` 建立 m*n 的基元列阵
* `diag(m,n)` 建立 m*n 的对角矩阵或提取对角元
* `logspace(a,b,n)` 生成 (a,b) 范围内的对数n等分的行向量
* `linspace(a,b,n)` 生成在 ab 间的等间距的n个数构成的行向量

`linspace(a,b,n)` 的效果和 `a:step:b` 类似, 都会生成等间距的向量

## 列向量拓展为数据网格的方法

如果已有两个行向量 `x` `y` , 则可以通过这两个行向量张成一个二维数据网格. 事实上这个操作就是将 `x` 按列复制, 将 `y` 按行复制.
```matlab
>> x = [1,3,5]; y = [2,4,6];
>> [ X , Y ] = meshgrid(x, y)
X =
     1     3     5
     1     3     5
     1     3     5
Y =
     2     2     2
     4     4     4
     6     6     6
```

## 结构变量

类似于许多语言的 `structure` 结构, Matlab 也可以定义结构化数据.
```matlab
>> s = struct('strings',{'hello','yes'},'lengths',[5 3])
s = 
  struct with fields:
    strings: {'hello'  'yes'}
    lengths: [5 3]
>> s.lengths
ans =
     5     3
>> s.strings
ans =
  1×2 cell array
    {'hello'}    {'yes'}
```

对于已经定义好的结构变量, 如果需要在变量中创建新的, 可以直接通过

如上所示, 变量 `s` 被初始化为带有两个字段的结构变量, 在必要时还可以将结构变量作为矩阵元素使用.

## 矩阵元素选中

| 命令 | 作用 |
| :--------: | :-- |
|   A(i,j)   | 第i行j列元素 |
|   A(:,j)   | 第j列所有元素 |
|  A(2:4,j)  | 第2到4行的第j列元素 |
|  A(end,j)  | 第j列的最后一个元素 |
|    A(k)    | 矩阵按列向量排列后的第k个元素 |