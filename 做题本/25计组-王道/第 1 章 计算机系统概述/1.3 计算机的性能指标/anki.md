---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: 2024-11-17 11:45
updated: 2024-11-17 11:58
TARGET DECK: 刷题::25计组-王道::第 1 章 计算机系统概述::1.3 计算机的性能指标::anki
---
### 计算机的主要性能指标

#### 基本性能指标

Q: 基本性能指标包括哪些？
A: 基本性能指标包括机器字长、储存容量、吞吐量以及响应时间。
![](https://img.hwenyi.live/202407212145177.webp)

#### 机器字长

Q: 机器字长的定义是什么？
A: 机器字长是指CPU一次能够处理的二进制数据的位数，与CPU内部用于整数运算的算术逻辑单元ALU的位数和通用寄存器的宽度相等。
![](https://img.hwenyi.live/202407212121236.webp)

Q: 机器字长对计算机系统性能的影响有哪些？
A: ![](https://img.hwenyi.live/202407212121236.webp)
- 字长越长，数的表示范围越大，精度也越高。
- 字长影响计算速度。

#### 储存容量

Q: 储存容量的定义是什么？
A: 储存容量是指主存储器能够存储的最大信息量，通常以字节为单位。
![](https://img.hwenyi.live/202407212122165.webp)
![](https://img.hwenyi.live/202407212122757.webp)

Q: 如何计算主存储器的总容量？
A: 储存容量 = 存储字长 × 存储单元个数。
![](https://img.hwenyi.live/202407212122165.webp)
![](https://img.hwenyi.live/202407212122757.webp)

#### 响应时间

Q: 响应时间的定义是什么？
A: 响应时间是指从向计算机系统提交作业开始，到系统完成作业为止所需要的时间。
![](https://img.hwenyi.live/202407212123498.webp)

Q: 响应时间包括哪些部分？
A: 响应时间包括CPU时间和其他时间，CPU时间又分为CPU执行时间和系统CPU时间。
![](https://img.hwenyi.live/202407212123498.webp)

#### 练习题

Q: 存储器地址寄存器MAR的位数决定了什么？
A: MAR的位数决定了存储单元的数量，具体为 $2^{\text{MAR的位数}}$ 个。
![](https://img.hwenyi.live/202407212124473.webp)

### 与运算速度相关的性能指标

#### CPU时钟频率和时钟周期

Q: CPU时钟频率的定义是什么？
A: CPU时钟频率是指机器内部主时钟脉冲信号的频率，基本单位为赫兹（Hz）。
![](https://img.hwenyi.live/202407212129135.webp)
![](https://img.hwenyi.live/202407212130357.webp)

Q: CPU时钟周期的定义是什么？
A: CPU时钟周期是CPU时钟频率的倒数，表示CPU工作中的最小时间单位。
![](https://img.hwenyi.live/202407212129135.webp)
![](https://img.hwenyi.live/202407212130357.webp)

Q: 时钟频率和时钟周期之间的关系是什么？
A: 时钟周期 = 1 / 时钟频率。
![](https://img.hwenyi.live/202407212129135.webp)
![](https://img.hwenyi.live/202407212130357.webp)
![](https://img.hwenyi.live/202407212131909.webp)

#### CPI

Q: CPI的定义是什么？
A: CPI（Cycles Per Instruction）是执行一条指令所需的时钟周期数量。
![](https://img.hwenyi.live/202407212132752.webp)
![](https://img.hwenyi.live/202407212132108.webp)

Q: CPI的计算公式是什么？
A: CPI = 程序执行所需时钟周期数量 / 程序所包含的指令数量。
![](https://img.hwenyi.live/202407212136623.webp)
![](https://img.hwenyi.live/202407212132108.webp)
![](https://img.hwenyi.live/202407212132752.webp)

#### CPU执行时间

Q: CPU执行时间的定义是什么？
A: CPU执行时间是指真正用于用户程序的执行时间，不包括操作系统、内存和外部设备访问的时间。
![](https://img.hwenyi.live/202407212137292.webp)

Q: CPU执行时间的计算公式是什么？
A: CPU执行时间 = 程序执行所需时钟周期数量 / CPU时钟频率。
![](https://img.hwenyi.live/202407212137292.webp)
![](https://img.hwenyi.live/202407212140855.webp)
![](https://img.hwenyi.live/202407212141180.webp)
![](https://img.hwenyi.live/202407212141451.webp)

#### IPC

Q: IPC的定义是什么？
A: [[IPC]]（Instructions Per Cycle）是每个时钟周期能够执行的指令数量，是CPI的倒数。

#### MIPS

Q: MIPS的定义是什么？
A: MIPS（Million Instructions Per Second）是**每秒**执行的百万条指令数量
![](https://img.hwenyi.live/202407212142104.webp)

Q: MIPS的计算公式是什么？
A: MIPS = 主频 / CPI / 10^6
![](https://img.hwenyi.live/202407212143622.webp)
![](https://img.hwenyi.live/202407212142104.webp)

#### MFLOPS

Q: MFLOPS的定义是什么？
A: MFLOPS（Million Floating-point Operations Per Second）是每秒执行的百万次浮点运算数量。
![](https://img.hwenyi.live/202407212144325.webp)

Q: MFLOPS的计算公式是什么？
A: MFLOPS = 每秒执行的浮点运算次数 / 10^6。
![](https://img.hwenyi.live/202407212144325.webp)

#### 基准程序

Q: 基准程序的定义是什么？
A: 基准程序是一组特定的程序，用于评测计算机的性能，能够有效模拟计算机在处理实际任务时的表现。

### 408真题练习

Q: MIPS、CPI、IPC的定义及其关系是什么？
A: - MIPS：每秒执行的百万条指令。
- [[CPI]]：执行一条指令所需的时钟周期数量。
- [[IPC]]：每个时钟周期能够执行的指令数量，是CPI的倒数。

Q: 如何通过已知量[[主频]]计算MIPS？
A: 使用公式 MIPS = （主频 / CPI）/ 10^6) 进行计算。
![](https://img.hwenyi.live/202407212148107.webp)

