---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: 2024-11-17 07:54
updated: 2024-11-17 07:54
TARGET DECK: 刷题::25计组-王道::第 3 章 存储系统::3.2 主存储器::anki
---
## 3.2.1 SRAM 芯片和 DRAM 芯片

### 1. SRAM 的工作原理

Q: SRAM 的存储元是什么？
A: SRAM 的存储元是双稳态触发器，通常使用六晶体管 MOS 实现。
![](https://img.hwenyi.tech/202407301819798.webp)
![](https://img.hwenyi.tech/202407301821883.webp)

Q: SRAM 的特点是什么？
A: SRAM 的特点是存取速度快，但集成度低，功耗较大，价格昂贵。
![](https://img.hwenyi.tech/202407301821883.webp)

Q: SRAM 的主要用途是什么？
A: SRAM 主要用于高速缓冲存储器 (Cache)。

### 2. DRAM 的工作原理

Q: DRAM 的存储元是什么？
A: DRAM 的存储元是利用存储元电路中栅极电容上的电荷来存储信息的，通常只使用一个晶体管。
![](https://img.hwenyi.tech/202407291640170.webp)
![](https://img.hwenyi.tech/202407301850432.webp)

Q: DRAM 的特点是什么？
A: DRAM 的特点是集成度高，位价低，功耗低，但存取速度比 SRAM 慢，且必须定时刷新和读后再生。
![](https://img.hwenyi.tech/202407291640170.webp)
![](https://img.hwenyi.tech/202407301850432.webp)

### 3. DRAM 的刷新

Q: DRAM 为什么要刷新？
A: DRAM 电容上的电荷只能维持 $1 \sim  2\mathrm{\;{ms}}$，因此需要定时刷新以防止信息丢失。
![](https://img.hwenyi.tech/202407291640170.webp)

Q: DRAM 的刷新需要注意哪些问题？
A: 
- 刷新对 CPU 是透明的。
- DRAM 的刷新单位是行。
- 刷新操作类似于读操作，但又有所不同。
- 刷新时不需要选片。

### 2.2.3、DRAM 与 SRAM 的刷新

##### 2、每次刷新多少存储单元？介绍两种模型（含示例）

Q: DRAM 每次刷新多少存储单元？
A: DRAM 每次刷新一行存储单元。

Q: DRAM 的刷新模型有哪些？
A: 
1. 简单模型：每次刷新一行存储单元，效率低。
2. 行列地址模型：将地址译码器分为行地址译码器和列地址译码器，提高刷新效率。

Q: 行列地址模型有什么优点？
A: 行列地址模型可以有效减少刷新次数，提高刷新效率。

##### 3、如何刷新？

Q: DRAM 如何刷新？
A: DRAM 通过读出一行的信息后重新写入的方式进行刷新，占用 1 个读/写周期。

##### 4、在什么时刻刷新？（分散、集中、异步刷新）

Q: DRAM 的刷新方式有哪些？
A: 
1. 分散刷新：将一个存储器系统的工作周期分为两部分，前半部分用于正常的读/写操作，后半部分用于刷新。
2. 集中刷新：在一个刷新周期内，利用一段固定的时间，依次对存储器的所有行进行逐一再生，在此期间停止对存储器的读/写操作。
3. 异步刷新：结合了前两种方法，在一个刷新周期内每一行仅刷新一次。

Q: 分散刷新的优点是什么？
A: 分散刷新没有死区。
![](https://img.hwenyi.tech/202407301845562.webp)

Q: 分散刷新的缺点是什么？
A: 分散刷新加长了系统的存取周期。
![](https://img.hwenyi.tech/202407301845562.webp)

Q: 集中刷新的优点是什么？
A: 集中刷新不受刷新工作的影响。
![](https://img.hwenyi.tech/202407301844849.webp)

Q: 集中刷新的缺点是什么？
A: 集中刷新期间（死区）不能访问存储器。
![](https://img.hwenyi.tech/202407301844849.webp)

Q: 异步刷新的优点是什么？
A: 异步刷新可以避免让 CPU 连续等待过长的时间。
![](https://img.hwenyi.tech/202407301848091.webp)

Q: 异步刷新的缺点是什么？
A: 异步刷新实现较为复杂。
![](https://img.hwenyi.tech/202407301848091.webp)

### 4. SDRAM

Q: SDRAM 的特点是什么？
A: SDRAM 与 CPU 采用**同步方式交换数据**，支持突发传输方式。
![](https://img.hwenyi.tech/202407301920578.webp)

Q: SDRAM 的行缓冲器是什么？
A: 行缓冲器用来缓存指定行中整行的数据，其大小为 “列数×位平面数”，通常用 SRAM 实现。
![](https://img.hwenyi.tech/202407301752401.webp)

### 5. DRAM 芯片的读/写周期

Q: DRAM 芯片读/写周期中，各信号的时间关系应符合哪些要求？
A: ![](https://img.hwenyi.tech/202407301753321.webp)
![](https://img.hwenyi.tech/202407301933517.webp)
![](https://img.hwenyi.tech/202407301934145.webp)
- 行地址必须在 $\overline{\mathrm{{RAS}}}$ 有效前送到芯片的地址引脚。
- 列地址必须在 $\overline{\mathrm{{CAS}}}$ 有效前送到芯片的地址引脚。
- $\overline{\mathrm{{RAS}}}\text{、}\overline{\mathrm{{CAS}}}$ 应分别至少保持 ${t}_{\mathrm{{RAS}}}$ 和 ${t}_{\mathrm{{CAS}}}$ 的时间。
- 写数据必须在 $\overline{\mathrm{{CAS}}}$ 有效前在数据总线上保持稳定。
![动画.webp](https://img.hwenyi.tech/202407301926008.webp)

### 6. SRAM 和 DRAM 的比较

Q: SRAM 和 DRAM 的主要区别是什么？
A: ![](https://img.hwenyi.tech/202407301753601.webp)
- 存储信息：SRAM 使用触发器，DRAM 使用电容。
- 破坏性读出：SRAM 非破坏性读出，DRAM 破坏性读出。
- 刷新：SRAM 不需要刷新，DRAM 需要刷新。
- 速度：SRAM 速度快，DRAM 速度慢。
- 集成度：SRAM 集成度低，DRAM 集成度高。
- 成本：SRAM 成本高，DRAM 成本低。
- 用途：SRAM 用于高速缓存，DRAM 用于主机内存。
![](https://img.hwenyi.tech/202407291640173.webp)
一方面：存储元件上导致的区别，也就是读数据是否需要重写的情况，DRAM 在读数据后需要有一个重写操作，而 SRAM 无需重写。
**另一方面**：
- 制造成本：DRAM 只需要一个电容，SRAM 需要 6 个 MOS 管，可以看出 DRAM 成本更低，SRAM 成本高。
- 集成度：DRAM 的电容很小，对比 SRAM 的小了很多，同样一块位置肯定是 DRAM 的电容数量更多，所以 DRAM 的集成度高，SRAM 集成度低。
- 功耗：DRAM 对比 SRAM 所需的功耗更低，因为其元器件对比 SRAM 的少。

### 7. 存储器芯片的内部结构

Q: 存储器芯片的内部结构有哪些部分？
A: ![](https://img.hwenyi.tech/202407301754704.webp)
1. 存储体
2. I/O 控制电路
3. 地址译码器
4. 片选控制信号
5. 读/写控制信号
![](https://img.hwenyi.tech/202407301850432.webp)

Q: 地址译码方式有哪些？
A: ![](https://img.hwenyi.tech/202407301754834.webp)
- 单译码法
- 双译码法
![](https://img.hwenyi.tech/202407301813682.webp)
![](https://img.hwenyi.tech/202407291640185.webp)

Q: 片选控制信号的作用是什么？
A: 片选控制信号用于选择被访问的芯片。
![](https://img.hwenyi.tech/202407301755852.webp)

Q: 读/写控制信号的作用是什么？
A: 读/写控制信号用于控制被选中单元进行读或写。
![](https://img.hwenyi.tech/202407301755066.webp)

## 3.2.2 只读存储器

### 1. 只读存储器 (ROM) 的特点

Q: ROM 的特点是什么？
A: ROM 的特点是结构简单、位密度高、非易失性、可靠性高。

Q: ROM 和 RAM 有什么区别？
A: ROM 和 RAM 都**是支持随机访问的存储器**，但 ROM 的内容一旦写入就不能轻易改变，即使掉电也不会丢失。

### 2. ROM 的类型

Q: ROM 可分为哪几类？
A: ![](https://img.hwenyi.tech/202407301952257.webp)
1. 掩模式只读存储器 (MROM)
2. 一次可编程只读存储器 (PROM)
3. 可擦除可编程只读存储器 (EPROM)
4. Flash 存储器
5. 固态硬盘 (SSD)

### 3. 掩模式只读存储器 (MROM)

Q: MROM 的特点是什么？
A: MROM 的内容由半导体制造厂按用户提出的要求在芯片的生产过程中直接写入，**写入以后任何人都无法改变其内容**。

### 4. 一次可编程只读存储器 (PROM)

Q: PROM 的特点是什么？
A: PROM 是可以实现一次性编程的只读存储器，允许**用户**利用专门的设备 (编程器) 写入自己的程序，**一旦写入，内容就无法改变。**

### 5. 可擦除可编程只读存储器 (EPROM)

Q: EPROM 的特点是什么？
A: EPROM 不仅可以由用户利用编程器写入信息，而且可以**对其内容进行多次改写。**

### 6. Flash 存储器

Q: Flash 存储器的特点是什么？
A: Flash 存储器是在 EPROM 的基础上发展起来的，**兼有 ROM 和 RAM 的优点，可以在不加电的情况下长期保存信息，又能在线进行快速擦除与重写。**

### 7. 固态硬盘 (SSD)

Q: 固态硬盘 (SSD) 的特点是什么？
A: 固态硬盘 (SSD) 是用固态电子存储芯片阵列制成的硬盘，由**控制单元和存储单元 (Flash 芯片) 组成**，保留了 Flash 存储器长期保存信息、快速擦除与重写的特性，对比传统硬盘也具有读/写速度快、低功耗的特性。

## 3.2.3 主存储器的基本组成

### 1. 主存储器的基本组成

Q: 主存储器的核心部件是什么？
A: 主存储器的核心部件是**存储矩阵**，由一个个存储 0 或 1 的记忆单元（也称存储元件）构成。
![](https://img.hwenyi.tech/202407301758325.webp)

Q: 存储元件(记忆单元)是什么？
A: 存储元件是具有两种稳态的能表示二进制 0 和 1 的物理器件。
![](https://img.hwenyi.tech/202407301758325.webp)

Q: 现代计算机通常采用什么编址方式？
A: 现代计算机通常采用字节编址方式，此时存储体中内的一个地址中有一个字节。
![](https://img.hwenyi.tech/202407301758325.webp)

### 2. 主存储器的工作原理

Q: CPU 如何访问主存储器？
A: ![](https://img.hwenyi.tech/202407301758325.webp)
1. CPU 将被访问单元的地址送到 MAR 中。
2. CPU 通过地址线将主存地址送到主存中的地址寄存器。
3. 地址译码器进行译码，选中相应单元。
4. CPU 将读/写信号通过控制线送到主存的读/写控制电路。
5. 若为写操作，CPU 将要写的信息送到 MDR 中，并写入选中的单元。
6. 若为读操作，主存读出选中单元的内容并送到 MDR 中。

Q: MAR 和 MDR 的位数分别与什么相同？
A: **MDR 的位数与数据线**的位数相同，**MAR 的位数与地址线**的位数相同。
![](https://img.hwenyi.tech/202407301758325.webp)
![](https://img.hwenyi.tech/202407301801721.webp)

Q: 地址线的位数决定了什么？
A: 地址线的位数决定了主存地址空间的最大可寻址范围。
![](https://img.hwenyi.tech/202407301801721.webp)

### 3. DRAM 芯片的地址引脚复用技术

Q: DRAM 芯片为什么要采用**地址引脚复用**技术？
A: DRAM 芯片容量较大，地址位数较多，为了减少芯片的地址引脚数，通常采用地址引脚复用技术。
![](https://img.hwenyi.tech/202407301915533.webp)

Q: 地址引脚复用技术的原理是什么？
A: 行地址和列地址通过**相同的引脚分先后两次输入**，这样地址引脚数可减少一半。
![](https://img.hwenyi.tech/202407301915533.webp)

### 4. DRAM 芯片行、列数的优化原则

Q: DRAM 芯片行、列数的优化原则是什么？
A: ![](https://img.hwenyi.tech/202407301915533.webp)
- 尽量使行、列位数相同，即满足 $| {r - c}|$ 最小。
- 使行数较少，即满足 $r \leq  c$。
![](https://img.hwenyi.tech/202407301918858.webp)
![](https://img.hwenyi.tech/202407301813682.webp)
![](https://img.hwenyi.tech/202407291640185.webp)

Q: DRAM 芯片为什么要使行、列位数相同？
A: 为了减少地址引脚数。
![](https://img.hwenyi.tech/202407301918858.webp)
![](https://img.hwenyi.tech/202407301915533.webp)

Q: DRAM 芯片为什么要行地址数较少？
A: 为了减少刷新开销。
![](https://img.hwenyi.tech/202407301915533.webp)
![](https://img.hwenyi.tech/202407301918858.webp)

## 3.2.4 多模块存储器

### 3. 双端口存储器

Q: 双端口存储器是什么？
A: 双端口存储器是指同一个存储器具有两个相互独立的存储器端口，每个端口都具有自己独立的数据总线、地址总线和控制总线。
![](https://img.hwenyi.tech/202407311511591.webp)

双端口存储器每个端口==可以独立==的进行读写操作。

Q: 双端口存储器如何解决读写冲突问题？
A: 可以为每个端口添加一个忙标志（busy），通过这种方法就可以解决读写冲突问题。
![](https://img.hwenyi.tech/202407311511591.webp)

Q: 双端口存储器如何决定哪个端口优先进行读写操作？
A: 由判断逻辑决定哪个端口优先进行读写操作，而将另一个端口的 B 类信号输出低电平，以延迟该端口对存储器的访问。
![](https://img.hwenyi.tech/202407311511591.webp)

Q: 双端口存储器的访问速度提高了多少？
A: 访问速度不可能提高一倍，因为冲突访问是不可避免的。
![](https://img.hwenyi.tech/202407311511591.webp)

### 1. 单体多字存储器

Q: 单体多字存储器是什么？  
A: 单体多字存储器是**指多个存储模块共享地址总线，按同一地址并行访问不同存储模块的同一单元，从而实现同一个存取周期内访问多个存储字**。
![](https://img.hwenyi.tech/202407311517521.webp)
![](https://img.hwenyi.tech/202407311517603.webp)

单体多字存储器的构造和==位扩展==的方式完全一样

Q: 单体多字存储器的原理是什么？  
A: 多个存储模块共享地址总线，按**同一地址并行访问不同存储模块的同一单元**，从而实现同**一个存取周期内访问多个存储字**。
![](https://img.hwenyi.tech/202407311517603.webp)

Q: 单体多字存储器的特点是什么？
A: 单体多字存储器的特点是每个存储单元存储 $m$ 个字，总线宽度也为 $m$ 个字，一次并行读出 $m$ 个字。
![](https://img.hwenyi.tech/202407311517603.webp)

Q: 单体多字存储器可以提高存储带宽多少倍？  
A: 如果有 N 个存储模块，则按单体多字存储器的方法，可将储存带宽提高 N 倍。

### 2. 多体并行存储器

Q: 多体并行存储器的特点是什么？
A: 多体并行存储器的特点是由**多个结构完全相同的存储模块的并行工作**来提高存储器的吞吐率。

Q: 多体并行存储器分为哪两种？
A: 
1. 高位交叉编址（顺序方式）
2. 低位交叉编址（交叉方式）

### （1）高位交叉编址（顺序方式）

Q: 高位交叉编址的特点是什么？
A: 主存地址由模块地址和块内地址两部分构成。
高位交叉编址的特点是总把低位的体内地址送到由高位体号确定的模块内进行译码。
- 不同存储模块对应不同的地址空间
- 将地址顺序分配给一个存储模块后，按顺序为下一个存储模块分配地址
- 又称为顺序编制模式
![](https://img.hwenyi.tech/202407311548461.webp)

Q: 高位多体交叉存储器的模块地址和块内地址的作用是什么？  
A: 模块地址用于区分不同的存储模块，块内地址用于区分存储单元。
![](https://img.hwenyi.tech/202407311547439.webp)
![](https://img.hwenyi.tech/202407311548461.webp)

Q: 高位交叉编址的缺点是什么？
A: 由于程序具有局部性和连续性的特点，因此采用高位多体交叉，也就是顺序编制模式。 
**程序的指令和数据基本分布在同一个储存模块中**，这样就会导致在程序执行过程中，**同一个储存模块被频繁访问**，**而其他储存模块基本处于空闲状态**，**无法实现多个储存模块的并行工作**。
![](https://img.hwenyi.tech/202407311548461.webp)

### （2）低位交叉编址（交叉方式）

Q: 低位多体交叉存储器是什么？  
A: 低位多体交叉存储器是多体交叉存储器的一种，它通过将存储地址的模块地址部分与块内地址部分编制顺序进行调整，从而实现多个存储模块的并行工作。
![](https://img.hwenyi.tech/202407311623078.webp)
![](https://img.hwenyi.tech/202408011520528.webp)
![](https://img.hwenyi.tech/202407311547439.webp)

Q:低位多体交叉存储器的特点是什么？  
A:![](https://img.hwenyi.tech/202407311623078.webp)
![](https://img.hwenyi.tech/202407311547439.webp)
- 存储地址的低位给各存储模块编号
- 存储地址的高位给各存储模块内的存储单元进行编制
- 各存储模块均有独立的地址寄存器、数据寄存器和读写控制电路
- 各存储模块一般按流水线的方式轮流存取
![](https://img.hwenyi.tech/202407311628352.webp)
![](https://img.hwenyi.tech/202408011520528.webp)

Q: 低位多体交叉存储器与高位多体交叉存储器有什么区别？  
A: **低位多体交叉存储器**将**存储地址的高位用于给各存储模块内的存储单元进行编址**，而主存地址的低位用于给各存储模块编号，而**高位多体交叉存储器**则是将存储地址的**高位用于给各存储模块编号，而主存地址的低位用于给各存储模块内的存储单元进行编址**
![](https://img.hwenyi.tech/202407311623078.webp)
![](https://img.hwenyi.tech/202407311547439.webp)

### 命题追踪 ___ 交叉存储器存取时间和带宽的计算 (2012、2013)

Q: 低位多体交叉存储器如何实现流水线访问？  
A: 各存储模块一般按流水线的方式轮流存取，每个模块的存**取周期为 T**，**其他延迟（例如总线传输周期等）总和**为 $\tau$，存储模块数量为 M。
要实现流水线方式存取，应满足条件 T 等于 M 乘以 $\tau$。
- 在一次流水线存取过程中，所有存储模块都被访问一次，不能重复访问某一个存储模块。
- 一次流水线存取过程总耗时为$t_{1} = T + (m - 1)\tau$
- 连续 N 次流水线存取过程总耗时为 N 倍的 $t_{1} = T + (m - 1)\tau$
![](https://img.hwenyi.tech/202407311625410.webp)
![](https://img.hwenyi.tech/202407311626639.webp)
注意！可从任意地址开始顺序读取，不一定非要从左到右
 ![动画.webp](https://img.hwenyi.tech/202407311629895.webp)

Q: 交叉存储器的存取时间如何计算？
A: 交叉存储器的存取时间为 $t_{1} = T + (m - 1)\tau$。
![动画.webp](https://img.hwenyi.tech/202407311626639.webp)
![](https://img.hwenyi.tech/202407311625410.webp)

### 命题追踪 交叉存储器中访存冲突的分析（2015）

Q: 交叉存储器中访存冲突的分析是什么？
A: ![](https://img.hwenyi.tech/202407311632585.webp)
- 访存冲突是指相邻的 $m$ 次访问的访存地址出现在同一个模块内。
- 访存冲突会导致延迟发生冲突的访问请求。
