---
layout: post
title: "微机原理设计实践"
subtitle:   "简易报警系统的软硬件设计"
header-img: "resources/microcomputer.jpg"
date:   2019-12-21 00:09:00 +0800
tags:
    - Micro Computer
    - MyCourses
---

## 需求描述

利用 `8255` 和 `8253` 可编程并行接口设计一个简易的安全报警系统. 功能要求:

* 在房间门窗等 `8个` 入口处安装探测器. 正常情况下, 探测器输出为 _低电平_ . 当探测到异常时, 探测器输出高电平. 此时, 启动报警(警铃响, 警灯闪烁), 并在危险解除(有任意键按下)后关闭报警;

* 当外部向 `8255` 的 `PC0` 端输入低电平时(可利用开关实现), 监控系统启动. 
系统启动后, 在初始状态下, 警铃不响, 警灯不亮. 系统不断检测各探测器的输出电平, 如果检测到有任意一个探测器的输出为高电平, 并且在随后的 `5次连续检测` 中, 该探测器的输出都为高电平, 则通过 `8255` 的 `PC6` 启动报警(`PC6` 输出高电平), 使 `8253` `通道0` 产生 `1kHz` 频率的方波, 控制警铃发出警报声. 由 `8255` 的 `PC7` 控制警报灯闪 (`PC7` 输出高电平时警灯亮). 

> 设: `8255` 的端口地址为 `380H` ～ `383H`. `8253` 的端口地址为 `384H` ～ `387H` . 外部时钟脉冲 `2MHz`. 

## 硬件连接

![电路图](/resources/microcomputer/circuit_design.svg)

## 功能分析

### 程序的总体架构

1. 程序需要两个循环, 第一个循环用来等待 `PC0` 端输入低电平, 第二个循环作为 **`主循环`**, 监控 `8` 个传感器的状态和键盘按键的状态, 并按要求输出警报信号.

2. 由于等待循环需要判断 `8255` 的 `PC0` 电平, 所以在进入 **`等待循环`** 前就应该完成 `8255` 和 `8253` 芯片的初始化.
    > 根据以上两条, 我们需要:
    >
    > ```nasm
    > ; 假设各个段寄存器已经设置完毕
    >
    > START:
    >   call  INIT        ; 初始化接口
    >   call  WAIT_CIRCLE ; 进入等待循环
    >   call  MAIN_CIRCLE ; 进入主循环
    >   jmp   EXIT        ; 退出
    > ```

3. 由于题目要求 `连续五次` 检测到 `同一个` 传感器输出高电平, 才触发报警信号, 且需要控制警灯闪烁, 因此, 我们需要 `8` 个字节来分别记录各个传感器先前的状态, 还需要一个 `WORD` 长度的计数器作为警灯闪烁的定时器.
    > 所以:
    >
    > ```nasm
    > DSEG SEGMENT
    >   Sensor  DB 0 DUP 8
    >           ; 每个Byte对应一个传感器,
    >           ; 如果当前循环传感器触发, 相应Byte + 1,
    >           ; 如果传感器没有触发, 相应Byte清零,
    >           ; 任意Byte>=5 触发警报.
    >   Counter DW 0
    >           ; 循环计数器.
    > DSEG ENDS
    > ```

### 循环子程序的流程图

![流程图](/resources/microcomputer/flow_chart.svg)

## 完整的汇编代码

```nasm
C255_1 equ 380H
C255_2 equ 381H
C255_3 equ 382H
C255_S equ 383H
C253_1 equ 384H
C253_2 equ 385H
C253_3 equ 386H
C253_S equ 387H
REPT_C equ 2000

DSEG SEGMENT
  Sensor  DB 0 DUP 8
          ; 每个Byte对应一个传感器,
          ; 如果当前循环传感器触发, 相应Byte + 1,
          ; 如果传感器没有触发, 相应Byte清零,
          ; 任意Byte>=5 触发警报.
  Counter DW 0
          ; 循环计数器.
DSEG ENDS

SSEG SEGMENT
    DB
SSEG 

CODE SEGMENT
    ASSUME cs:CODE, ds:DSEG, es:DSEG, ss:SSEG
START:
    mov  ax, DSEG
    mov  ds, ax
    mov  es, ax
    mov  ax, SSEG
    mov  ss, ax

    call INIT
    call WAIT_CIRCLE
    call MAIN_CIRCLE

INIT PROC
    mov  dx, C255_S
    mov  al, 00000000B
    out  dx, al
    mov  dx, C253_S
    mov  al, 00000000B
    out  dx, al
    ret
ENDP

WAIT_CIRCLE PROC
    
    ret
ENDP

MAIN_CIRCLE PROC
    
    ret
ENDP
CODE ENDS
END START
```