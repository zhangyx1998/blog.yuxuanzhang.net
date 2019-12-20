---
layout: post
title:  "微机原理课程相关"
subtitle:   "Topic of course 'Micro Computer Principals'"
# header-img: "img/xxx.jpg"
date:   2019-12-20 16:25:00 +0800
tags:
    - Micro Computer
    - MyCourses
---

## 8255芯片

### 8255芯片寻址方式

8255有三组输入输出接口和一个控制寄存器, 因此只需两根地址线即可寻址.

| A<sub>0</sub> | A<sub>0</sub> | 选中 |
| :-: | :-: | :-: |
| 0 | 0 | A组 |
| 0 | 1 | B组 |
| 1 | 0 | C组 |
| 1 | 1 | 控制寄存器 |

