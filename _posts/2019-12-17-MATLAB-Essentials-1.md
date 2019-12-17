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


### Matlab的基本语法

与Javascript类似,Matlab变量使用前不需要声明,第一次向变量赋值的同时变量就被创建.

所有变量均为矩阵变量,如果定义了一维常数变量`a = 1`,则等同于定义了`a[0,0] = 1`.

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