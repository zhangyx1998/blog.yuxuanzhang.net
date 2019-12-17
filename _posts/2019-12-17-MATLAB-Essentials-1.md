---
layout: post
title:  "MATLAB Essentials 1"
subtitle:   "基本语法和数据结构"
header-img: "resources/matlab.png"
date:   2019-12-17 15:30:00 +0800
tags:
    - MATLAB
    - PHYSICS
---

### Index of _Matlab Essentials_
* **基本语法和数据结构(本文)**
* [Matlab常用函数](./MATLAB-Essentials-2.html)
* [具体应用](./MATLAB-Essentials-3.html)

### Matlab 的变量

与 Javascript 类似, Matlab 变量使用前不需要声明, 第一次向变量赋值的同时变量就被创建. Matlab 的所有变量均为矩阵变量, 如果定义了一维常数变量 `a = 1` , 则等同于定义了1*1的矩阵变量 `a = [1]` .

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

### Matlab 基本运算符

变量之间的运算符主要有 `+ - * / .* ./` 其中 `.* ./` 为点乘点除,正常写法的乘除为矩阵运算.

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

### 初始化矩阵的几种命令

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

### 矩阵元素标识(选中)

| 命令 | 作用 |
| :--------: | :-- |
|   A(i,j)   | 第i行j列元素 |
|   A(:,j)   | 第j列所有元素 |
|  A(2:4,j)  | 第2到4行的第j列元素 |
|  A(end,j)  | 第j列的最后一个元素 |
|    A(k)    | 矩阵按列向量排列后的第k个元素 |