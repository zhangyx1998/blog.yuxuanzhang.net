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

* 在房间门窗等 `8个` 入口处安装探测器. 正常情况下, 探测器输出为 _低电平_ . 当探测到异常时, 探测器输出 _高电平_ . 此时, 启动报警(警铃响, 警灯闪烁), 并在危险解除(有任意键按下)后关闭报警;

* 当外部向 `8255` 的 `PC0` 端输入 _低电平_ 时(可利用开关实现), 监控系统启动. 
系统启动后, 在初始状态下, 警铃不响, 警灯不亮. 系统不断检测各探测器的输出电平, 如果检测到有任意一个探测器的输出为 _高电平_ , 并且在随后的 `连续5次检测` 中, 该探测器的输出都为 _高电平_ , 则通过 `8255` 的 `PC6` 启动报警(`PC6` 输出 _高电平_ ), 使 `8253` `通道0` 产生 `1kHz` 频率的方波, 控制警铃发出警报声. 由 `8255` 的 `PC7` 控制警报灯闪 (`PC7` 输出高电平时警灯亮). 

> 设: `8255` 的端口地址为 `380H` ～ `383H`. `8253` 的端口地址为 `384H` ～ `387H` . 外部时钟脉冲 `2MHz`. 

## 硬件连接

![电路图](/resources/microcomputer/circuit_design.svg)

### 地址验证:

* `8255` 端口地址为 `0380H` ～ `0383H`, 转化为16位二进制, 即:
  
    > `0011 1000 0000B` ～ `0011 1000 0011B`
    
    片选有效的条件是

    > ```plain
    > A15 A14 A13 A12 A11 A10 A09 A08 A07 A06 A05 A04 A03 A02 A01 A00
    >  0   0   1   1   1   0   0   0   0   0   0   0   0   0   X   X
    > ```

* `8253` 端口地址为 `0384H` ～ `0387H`, 转化为16位二进制, 即:
  
    > `0011 1000 0100B` ～ `0011 1000 0111B`
     
    片选有效的条件是

    > ```plain
    > A15 A14 A13 A12 A11 A10 A09 A08 A07 A06 A05 A04 A03 A02 A01 A00
    >  0   0   1   1   1   0   0   0   0   0   0   0   0   1   X   X
    > ```

上图所示电路的寻址功能满足要求.

## 功能分析

### 程序的总体架构

1. 程序需要两个循环, 第一个循环(**`等待循环`**)用来等待 `PC0` 端输入低电平, 第二个循环作为 **`主循环`**, 监控 `8` 个传感器的状态和键盘按键的状态, 并按要求输出警报信号.

2. 由于 **`等待循环`** 需要判断 `8255` 的 `PC0` 电平, 所以在进入 **`等待循环`** 前就应该完成 `8255` 和 `8253` 芯片的初始化.
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
    >   Sensor  DB 8 DUP 0
    >           ; 每个Byte对应一个传感器,
    >           ; 如果当前循环传感器触发, 相应Byte + 1,
    >           ; 如果传感器没有触发, 相应Byte清零,
    >           ; 任意Byte>=5 触发警报.
    >   Counter DD 0
    >           ; 循环计数器.
    > DSEG ENDS
    > ```

### 循环子程序的流程图

![流程图](/resources/microcomputer/flow_chart.svg)

## 完整的汇编代码

```nasm
; 8255芯片地址
C8255_A EQU 380H
C8255_B EQU 381H
C8255_C EQU 382H
C8255_S EQU 383H
; 8253芯片地址
C8253_0 EQU 384H
C8253_1 EQU 385H
C8253_2 EQU 386H
C8253_S EQU 387H
; 8253 产生 1kHz 脉冲对应的计数器值
REP_C   EQU 2000

DSEG SEGMENT
  Sensor  DB 8 DUP (0)
          ; 每个Byte对应一个传感器,
          ; 如果当前循环传感器触发, 相应Byte + 1,
          ; 如果传感器没有触发, 相应Byte清零,
          ; 任意Byte>=5 触发警报.
  Counter DD 0
          ; 循环计数器.
DSEG ENDS

SSEG SEGMENT
    DB ?
SSEG ENDS

CODE SEGMENT
    ASSUME CS:CODE, DS:DSEG, ES:DSEG, SS:SSEG
START:
    MOV  AX, DSEG
    MOV  DS, AX
    MOV  ES, AX
    MOV  AX, SSEG
    MOV  SS, AX
    ; 以下为主要程序逻辑
    CALL INIT
    CALL WAIT_CIRCLE
    CALL MAIN_CIRCLE
; EXIT事实上永远不会执行
EXIT:
    MOV  AX, 4C00H
    INT  21H

INIT PROC
    ; 写8255设置寄存器
    MOV  DX, C8255_S
    MOV  AL, 10010001B
    OUT  DX, AL
    ; 为8255_PC高四位清零
    MOV  DX, C8253_C
    MOV  AL, 00H
    OUT  DX, AL
    ; 写8253设置寄存器
    MOV  DX, C8253_S
    MOV  AL, 00110110B ; 0组 先低后高 方式3 二进制
    OUT  DX, AL
    ; 为8253方波发生器赋频率值
    MOV  DX, C8253_0
    MOV  AX, REP_C
    OUT  DX, AL
    MOV  AL, AH
    OUT  DX, AL
    RET
ENDP

WAIT_CIRCLE PROC
    MOV  DX, C8255_C
WC_LOOP:
    IN   AL, DX
    AND  AL, 00000001B ; 滤出PC0
    JNZ  WC_LOOP
    RET
ENDP

MAIN_CIRCLE PROC
; 检测循环
MC_CHECK:
    MOV  DX, C8255_A
    IN   AL, DX
    CALL QUALIFY
    CMP  AH, 0
    JE   MC_CHECK

; 警报循环
MC_ALERT:
    ; 检测键盘按键是否按下
    MOV  AH, 08H
    INT  21H
    TEST AL, 0FFH
    JNZ  MC_FINAL
    ; 计数, 控制灯闪烁
    MOV  AX, WORD PTR Counter
    INC  AX
    MOV  WORD PTR Counter, AX
    MOV  AX, WORD PTR Counter[1]
    ADC  AX, 0
    MOV  WORD PTR Counter[1], AX
    AND  AX, 8000H
    MOV  AL, AH
    OR   AL, 01000000B ; SET PC6 = High
    MOV  DX, C8255_C
    OUT  DX, AL
    JMP  MC_ALERT
; 清空Sensor变量, 关警报, 准备进入下一个检测循环
MC_FINAL:
    MOV  DX, C8255_C
    MOV  AL, 00H
    OUT  DX, AL
    CALL CLEAR
    JMP  MC_CHECK
    RET
ENDP

QUALIFY PROC
    ; AL存放当前8个传感器的状态
    ; 子程序结束后 AH = 0 表示不符合报警条件
    ;            AH > 0 表示报警
    PUSH BX
    PUSH CX
    XOR  AH, AH
    XOR  BX, BX
QF_LOOP:
    MOV  CL, Sensor[BX]
    SHR  AL
    JNC  QF_NEXT
    INC  CL
    MOV  Sensor[BX], CL
QF_NEXT:
    ADD  CL, 0FFH - 5 + 1
    ADC  AH, 0
    INC  BX
    CMP  BX, 8
    JL   QF_LOOP
QF_FINAL:
    POP  CX
    POP  BX
    RET
ENDP

CLEAR PROC
    PUSH CX
    PUSH BX
    MOV  CX, 8
    XOR  BX, BX
CL_LOOP:
    MOV  Sensor[BX], 0
    INC  BX
    LOOP CL_LOOP
CL_FINAL:
    POP  BX
    POP  CX
    RET
ENDP

CODE ENDS
END START
```