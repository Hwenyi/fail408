---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: "2024-12-03 13:09"
updated: "2024-12-03 13:45"
---
## 1.1 内存的基础知识

### 1.1.2 进程运行的基本原理

#### 1.1.2.2 逻辑地址与物理地址

Q: 什么是逻辑地址？
A: 程序员看到的地址，是相对于程序起始地址的偏移量。
![](https://img.hwenyi.tech/202407291607724.webp)

#### 1.1.2.3 从写程序到程序运行

Q: 程序从编写到运行的步骤是什么？
A: 编译 → 链接 → 装入

Q: 编译的作用是什么？
A: 将源代码翻译成目标模块。
![](https://img.hwenyi.tech/202407291607725.webp)

Q: 链接的作用是什么？
A: 将目标模块和库函数链接成一个完整的装入模块。
![](https://img.hwenyi.tech/202407291607725.webp)

Q: 装入的作用是什么？
A: 将装入模块装入内存。
![](https://img.hwenyi.tech/202407291607725.webp)

#### 1.1.2.4 三种链接方式

Q: 静态链接是什么？
A: 在程序运行前将所有目标模块和库函数链接成一个完整的可执行文件。
![](https://img.hwenyi.tech/202407291607726.webp)
其中并没有提前链接成一整个大的装入模块，而是在**装入内存时链接**
完整的逻辑地址是一边装入内存一边形成的

Q: 装入时动态链接是什么？
A: 在程序装入内存时进行链接。
![](https://img.hwenyi.tech/202407291607727.webp)

Q:运行时动态链接是什么？
A:在程序执行中只有需要到该目标模块时，才进行链接。
![](https://img.hwenyi.tech/202407291607728.webp)
优点：便于修改和更新，便于实现对目标模块的共享，可以提升对内存的利用率。

#### 1.1.2.5 三种装入方式

Q: 绝对装入的特点是什么？
A: 在编译时就知道程序的绝对地址，直接生成绝对地址的目标代码。
![](https://img.hwenyi.tech/202407291607729.webp)
**评价**：绝对装入只适合单道程序环境。
- 若是换一个系统环境，那么原本编译得到的绝对地址那么就极有可能失效。
注意：最终修改后的绝对地址实际上是**直接存储在**装入模块（非内存），**可执行文件中**的（exe）。

Q: 静态重定位的特点是什么？
A: 在装入时将逻辑地址转换为物理地址。
![](https://img.hwenyi.tech/202407291607730.webp)

Q: 动态重定位(又称为动态运行时装入)的特点是什么？
A: 又称为动态运行时装入，在程序执行时才将逻辑地址转换为物理地址。
![](https://img.hwenyi.tech/202407291607731.webp)
与其他不同的是多加了一个**重定位寄存器，用于存放装入模块程序的起始地址**。
时机：在真正指令读取执行的时候，当读取到逻辑地址为 79 的时候，会将重定位寄存器中的地址相加，最终得到一个绝对地址。

## 1.2 内存管理的概念

### 内存管理的四个功能

Q: 操作系统在内存管理方面主要负责哪些功能？
A: 内存空间的分配与回收、内存空间的扩充、地址转换、存储保护。
![](https://img.hwenyi.tech/202407291607744.webp)

Q: 地址转换(逻辑地址和虚拟地址)的实现方式有哪些？
A: 绝对装入、静态重定位、动态重定位。

### ④ 存储保护

Q: 存储保护的两种方式是什么？
A: 
1. 使用上、下限寄存器。
2. 使用重定位寄存器和界地址寄存器。

## 1.3 覆盖与交换

### 1.3.1 覆盖技术

Q: 覆盖技术是为了解决什么问题？
A: 解决程序大小超过物理内存总和的问题。
![](https://img.hwenyi.tech/202407291607740.webp)

Q: 覆盖技术的基本思想是什么？
A: 将程序划分为多个段，常用的段常驻内存，不常用的段需要时调入内存。

### 1.3.2 交换技术

Q: 交换技术的设计思想是什么？
A: 内存空间紧张时，将内存中某些进程暂时换出到外存，把外存中某些已具备运行条件的进程换入内存。

Q: 交换技术对应哪种进程调度？
A: 中级调度（内存调度）。
![](https://img.hwenyi.tech/202407291607741.webp)

Q: 为什么进程的 PCB 需要常驻内存？
A: 因为 PCB 中记录了进程在外存中的地址信息。
![](https://img.hwenyi.tech/202407291607741.webp)

Q: 交换技术中，被换出的进程通常存储在外存的哪个区域？
A: 对换区。
![](https://img.hwenyi.tech/202407291607741.webp)

Q: 交换技术中，对换区通常采用哪种分配方式？
A: 连续分配方式。
连续与非连续的区别：连续分配指的是给用户进程分配的是一个连续的内存空间；非连续分配则是分配的不连续的内存空间。
![](https://img.hwenyi.tech/202407291607745.webp)

Q: 交换技术中，应该换出哪些进程？
A: 优先换出阻塞进程、优先级低的进程，并考虑进程在内存的驻留时间等因素。
![](https://img.hwenyi.tech/202407291607744.webp)

# 补充

## 程序的链接与装入

Q: 三种装入方式分别是什么？
A: 绝对装入、可重定位装入、动态运行时装入。

## 逻辑地址与物理地址

Q: 什么是逻辑地址空间？
A: 逻辑地址空间是指由程序产生的与段相关的偏移地址部分。逻辑地址的集合就是逻辑地址空间。

Q: 什么是物理地址空间？
A: 物理地址空间是指内存中物理单元的集合。物理地址的集合就是物理地址空间。

## 进程的内存映像

Q: 一个进程的内存映像一般有哪几个要素？
A: 代码段、数据段、进程控制块 (PCB)、堆、栈。
![](https://img.hwenyi.tech/202407291547041.webp)

Q: 代码段的特点是什么？
A: 存放程序的二进制代码，代码段是只读的，可以被多个进程共享。
![](https://img.hwenyi.tech/202407291547041.webp)

Q: 数据段的特点是什么？
A: 存放程序运行时加工处理的对象，包括全局变量和静态变量。
![](https://img.hwenyi.tech/202407291547041.webp)

Q: 堆的特点是什么？
A: 用来存放动态分配的变量，通过调用 malloc 函数动态地向高地址分配空间。
![](https://img.hwenyi.tech/202407291547041.webp)

Q: 栈的特点是什么？
A: 用来实现函数调用，从用户空间的最大地址往低地址方向增长。
![](https://img.hwenyi.tech/202407291547041.webp)

## 内存保护

Q: 内存保护的两种方法是什么？
A: 1. 在 CPU 中设置一对上、下限寄存器，放用户进程在主存中的下限和上限地址, 每当 CPU 要访问一个地址时, 分别和两个寄存器的值相比, 判断有无越界。
2. 采用重定位寄存器和界地址寄存器进行越界检查。
  - 实现内存保护需要重定位寄存器和界地址寄存器, 因此要注意两者的区别。
    - 重定位寄存器是用来 “加” 的, 逻辑地址加上重定位寄存器中的值就能得到物理地址; 
    - 界地址寄存器是用来 “比” 的, 通过比较界地址寄存器中的值与逻辑地址的值来判断是否越界。
加载重定位寄存器和界地址寄存器时必须使用特权指令, 只有操作系统内核才可以加载这两个存储器。
这种方案允许操作系统内核修改这两个寄存器的值, 而不允许用户程序修改。
![0190de02-3c6a-77ee-9509-aa0f897ee3dc_192_204030.jpg](https://img.hwenyi.tech/202407291547042.webp)

## 内存共享

Q: 什么是可重入代码？
A: 一种允许多个进程同时访问但不允许被任何进程修改的代码，也称为纯代码。
可重入代码也称为纯代码，例如：`printf()`函数。

## 内存分配与回收

Q: 页式存储管理的特点是什么？
A: 将内存空间划分为大小相等的页面，以页面为单位进行内存分配。

Q: 分段存储管理的特点是什么？
A: 将程序按逻辑关系划分为若干个段，每个段都有一个段名和段号。

# 1.4、连续分配管理方式（三种方式，内存管理第一个功能扩充）

## 单一连续分配管理方式

Q: 操作系统中，什么是单一连续分配？
A: 单一连续分配是指将内存分为系统区和用户区，用户程序独占整个用户区。
![](https://img.hwenyi.tech/202407291607746.webp)
![](https://img.hwenyi.tech/202407291607747.webp)

Q: 单一连续分配方式的优缺点是什么？
A: **优点**：实现简单，无外部碎片，可以采用覆盖技术扩充内存。由于同一时刻只有一个用户程序在运行，所以采用这种分配方式的系统**不一定需要内存保护**。
缺点：只能用于单用户、单任务的操作系统，存在内部碎片，内存利用率低。

## 固定分区分配管理方式

Q: 什么是固定分区分配？
A: 固定分区分配是将内存用户空间划分为若干个固定大小的分区，每个分区只装入一道作业。
![](https://img.hwenyi.tech/202407291607748.webp)

Q: 固定分区分配方式分为哪两种？
A: 分区大小相等和分区大小不相等两种。
![](https://img.hwenyi.tech/202407291607748.webp)

Q: 固定分区分配方式中，操作系统如何记录内存分区的使用情况？
A: 通过分区说明表来记录，每个表项对应一个分区，包含分区大小、起始地址、状态等信息。
![](https://img.hwenyi.tech/202407291607749.webp)
![](https://img.hwenyi.tech/202407291607748.webp)

## 动态分区分配管理方式

### 动态分区分配的定义

Q: 什么是动态分区分配？
A: 动态分区分配又称为可变分区分配，是在进**程装入内存时**，根据**进程的大小动态地建立分区**，分区大小和数量可变。
![](https://img.hwenyi.tech/202407291607767.webp)
![](https://img.hwenyi.tech/202407291607750.webp)
**举例**：一个内存空间分为系统区和用户区，系统去占 8M 字节，用户区为 56M 字节，刚开始到达用户进程 1 为 20MB，进程 2 为 14MB，进程 3 为 18MB，此时整个内存还剩余 4MB。

### 动态分区分配的数据结构

Q: 动态分区分配中，常用的两种数据结构是什么？
A: 空闲分区表和空闲分区链。
![](https://img.hwenyi.tech/202407291607752.webp)
![](https://img.hwenyi.tech/202407291607751.webp)

Q: 空闲分区表的作用。
A: 空闲分区表记录每个空闲分区的分区号、大小、起始地址等信息。

Q: 空闲分区链的作用。
A: 空闲分区链中，每个空闲分区通过前向指针和后向指针链接，并记录分区大小等信息。

### 动态分区分配的算法

Q: 动态分区分配常用的四种算法是什么？
A: 首次适应算法、最佳适应算法、最快适应算法、邻近适应算法。
![](https://img.hwenyi.tech/202407291607767.webp)
![](https://img.hwenyi.tech/202407291607751.webp)

Q: 简述首次适应算法的思想和实现方式。
A: 思想：从低地址开始查找，**找到第一个能满足大小**的空闲分区。
实现：**空闲分区以地址递增的次序排列**。
![](https://img.hwenyi.tech/202407291607752.webp)
![](https://img.hwenyi.tech/202407291607754.webp)

四种动态分区算法中，==首次适应==算法的效果反而更好。

Q: 简述[[最佳适配|最佳适应]]算法的思想和实现方式，并说明其缺点。
A: 思想：**优先使用最小的空闲分区**，以保留大的空闲区。
实现：空闲分区**按容量递增次序链接**。
缺点：会产生很多外部碎片。
![](https://img.hwenyi.tech/202407291607757.webp)

Q: 简述最快适应算法的思想和实现方式，并说明其缺点。
A: 思想：优先使用最大的空闲分区。
实现：空闲分区**按容量递减次序链接**。
缺点：大空闲区容易被耗尽，不利于大进程。
![](https://img.hwenyi.tech/202407291607762.webp)
![](https://img.hwenyi.tech/202407291607763.webp)

Q: 简述[[循环首次适配|邻近适应]]算法的思想和实现方式，并说明其优缺点。
A: 思想：从上次查找结束的位置开始查找空闲分区。
实现：空闲分区按地址递增次序排列。
优点：减少查找开销，可能保留大空闲区。
缺点：可能导致外部碎片。
![](https://img.hwenyi.tech/202407291607765.webp)
![](https://img.hwenyi.tech/202407291607766.webp)

### 动态分区分配的优缺点

Q: 动态分区分配的优点是什么？
A: 没有**内部**碎片。
内部碎片：分配给某进程的一块内存区域中，如果有些部分没有用上。
![](https://img.hwenyi.tech/202407291607782.webp)

Q: 动态分区分配的缺点是什么？
A: 存在**外部**碎片，可能需要紧凑技术来解决。
外部碎片：指的是内存中某些空闲分区由于太小而难以利用。
![](https://img.hwenyi.tech/202407291607779.webp)
![](https://img.hwenyi.tech/202407291607782.webp)

### 紧凑技术

Q: 什么是紧凑技术？
A: 紧凑技术是将内存中的程序进行移动，合并外部碎片，以便容纳新的进程。
![](https://img.hwenyi.tech/202407291607781.webp)
`紧凑技术`过程应该是采用**动态重定位**的方式实现（可以回忆交换技术、换入 / 换出）。
- **实现方式就是**：在使用动态重定位的时候，需要将进程的起始地址修改，也就是在对应的 PCB 当中，当进程要上 CPU 运行之前，会把进程的起始地址放到重定位寄存器中。
![](https://img.hwenyi.tech/202407291607782.webp)

## 连续分配管理方式总结

Q: [[连续分配]]管理方式有哪些？
A: 单一连续分配、固定分区分配和动态分区分配。

Q: 连续分配管理方式的优点和缺点是什么？
A: 优点：实现简单。缺点：容易产生碎片（内部碎片或外部碎片），内存利用率低。

### 覆盖技术

Q: 什么是覆盖技术？
A: 覆盖技术是一种允许程序逻辑地址空间大于物理地址空间的技术，通过将程序划分为多个覆盖块，只将需要的覆盖块装入内存。
![](https://img.hwenyi.tech/202407291607740.webp)
若是程序有一个明显的调用结构，我们可以依据其自身的调用结构，让那些不可能同时被访问的程序段共享同一个覆盖区。

# 连续分配管理方式的anki卡片

## 动态分区分配

Q: 动态分区分配中，回收分区时，根据回收分区的始址，从空闲分区链中找到相应的插入点，可能出现哪几种情况？
A: 1. 回收区与插入点的前一空闲分区相邻，则合并，修改前一分区大小。
2. 回收区与插入点的后一空闲分区相邻，则合并，修改后一分区始址和大小。
3. 回收区同时与插入点的前、后两个空闲分区相邻，则合并三个分区，修改前一分区大小，并取消后一分区。
4. 回收区没有相邻的空闲分区，则新建一个表项插入空闲分区链。

Q: 动态分区分配中，按分区检索方式可分为哪两种分配算法？
A: 顺序分配算法和索引分配算法。
当系统很大时, 空闲分区链可能很长, 此时采用顺序分配算法可能很慢。因此, 在大、中型系统中往往采用索引分配算法。

Q: 动态分区分配中，常见的索引分配算法有哪些？
A: 快速适应算法、伙伴系统和哈希算法。

## 伙伴系统 (Buddy System)

Q: 什么是伙伴系统？
A: 伙伴系统是一种动态分区分配算法，规定所有分区的大小均为 2 的 k 次幂（k 为正整数）。分配和回收内存时，都以伙伴为单位进行操作。

Q: 伙伴系统是如何分配内存的？
A: 当需要分配大小为 n 的分区时，找到 2^(i-1) < n <= 2^i 的 i，在 2^i 的空闲分区链中查找。
若找到，则分配；否则，查找 2^(i+1) 的分区，若找到，则将其分割成两个伙伴，一个分配，一个加入 2^i 的空闲链；若未找到，则继续向上查找更大的分区。

Q: 伙伴系统是如何回收内存的？
A: 回收时，检查其伙伴是否空闲，若空闲则合并，并继续向上检查是否可以合并更大的伙伴。

### 连续分配管理方式总结

Q: 为什么说非连续分配方式的存储密度低于连续分配方式？
A: 因为非连续分配方式需要额外的空间去存储分散区域的索引，增加了内存管理的开销。

## 关于动态分区分配算法的补充说明

Q: 四种基本的动态分区分配算法中，哪一种算法的性能最好？
A: 首次适应算法（First Fit）的性能最好，开销小，回收分区也不需要对空闲分区重新排序。

Q: 最佳适应算法的缺点是什么？
A: 最佳适应算法虽然能更多地留下大空闲分区，但会产生最多的外部碎片，性能通常很差。

Q: 最坏适应算法的缺点是什么？
A: 最坏适应算法会很快导致没有大空闲分区可用，因此性能也很差。

## 关于索引分配算法的补充说明

Q: 快速适应算法的优缺点是什么？
A: 优点是查找效率高、不产生内部碎片；缺点是回收分区时，需要有效地合并分区，算法比较复杂，系统开销较大。
空闲分区的分类根据进程常用的空间大小进行划分。分配过程分为两步: 
①首先根据进程的长度, 在索引表中找到能容纳它的最小空闲分区链表; 
②然后从链表中取出第一块进行分配。优点是查找效率高、不产生内部碎片; 缺点是回收分区时, 需要有效地合并分区, 算法比较复杂, 系统开销较大。

# 1.5、非连续分配管理（三种方式，内存管理第一个功能扩充）

## 1.5.1、基本分页存储管理

## 1.5.1.1、基本分页存储管理的基本概念

## 基本概念

Q: 什么是页框(Page Frame)?
A: 页框是主存中划分的大小相等的分区，通常为 4KB，每个分区称为一个页框，也称为页帧、内存块、物理块、物理页面，编号从 0 开始。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 什么是页(Page)或页面?
A: 页或页面是进程逻辑地址空间中与页框大小相等的部分，每个称为一个页或页面，编号从 0 开始。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 页和页框的区别是什么?
A: 页是进程逻辑地址空间的划分，而页框是主存的物理划分。页框在主存中真实存在，而页不一定对应实际的物理页框，需要通过页表进行映射。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 什么是页框号(Page Frame Number)?
A: 页框号是页框的编号，从 0 开始，也称为页帧号、内存块号、物理块号、物理页号。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 什么是页号(Page Number)?
A: 页号是页面的编号，从 0 开始。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 什么是页表(Page Table)?
A: 页表是记录进程页面和内存页框之间映射关系的数据结构，通常**存在于 PCB（进程控制块）中**，每个进程都有一个页表。
![](https://img.hwenyi.tech/202407291607787.webp)

Q: 页表中每个页表项包含什么信息?
A: 每个页表项包含页号和块号(也称为页框号)。页号可以隐含
![](https://img.hwenyi.tech/202407291607787.webp)

## 逻辑地址到物理地址转换

Q: 逻辑地址如何构成?
A: 逻辑地址由页号和页内偏移量组成。
![](https://img.hwenyi.tech/202407291607790.webp)
![](https://img.hwenyi.tech/202407291607785.webp)
**回顾知识**：若是进程在**内存中连续存放**的时候，通过借助指令中的偏移量以及重定位寄存器中的值相加即可得到一个物理地址：
![](https://img.hwenyi.tech/202407291607789.webp)

Q: 如何通过页表将逻辑地址转换为物理地址?
A: 1. 确定逻辑地址的页号。
2. 根据页号在页表中查找对应的块号。
3. 将块号乘以内存块大小，得到该页面在内存中的起始地址。
4. 将页内偏移量加到起始地址，得到最终的物理地址。
**最终计算**：`逻辑地址A的物理地址 = P号页面在内存中的起始地址 + 页内偏移量 W`
![](https://img.hwenyi.tech/202407291607791.webp)

Q: 物理地址计算公式是什么？假设逻辑地址为 A，页号为 P，页内偏移量为 W，块号为 J，内存块大小为 S。
A: 物理地址 = J * S + W，其中 J 是通过页表根据页号 P 查找到的块号。
![](https://img.hwenyi.tech/202407291607792.webp)

Q: 如何优化逻辑地址到物理地址的转换过程?
A: 1. **页号计算优化**: 可以使用位移操作代替除法运算，例如 `页号 = 逻辑地址 >> 页面大小位数`。
2. **页内偏移量计算优化**: 可以使用位运算代替取余运算，例如 `页内偏移量 = 逻辑地址 & (页面大小 - 1)`。
3. **使用快表(TLB)**: 快表是一种高速缓存，用于存储最近访问的页表项，可以加速地址转换过程。

### 页面大小选择

Q: 为什么页面大小通常选择为 2 的整数幂?
A: 选择 2 的整数幂可以方便地使用位移操作进行计算，提高地址转换的效率。例如，如果页面大小为 4KB (2^12)，那么页内偏移量就是逻辑地址的低 12 位，页号就是逻辑地址的高位部分。
**若页面大小不是采用 2 的整数幂，那么我们只能使用土办法计算**：
![](https://img.hwenyi.tech/202407291607793.webp)
**对于页面大小刚好为 2 的整数幂更加详细的可以看下王道的说明**：
![](https://img.hwenyi.tech/202407291607794.webp)

### 考点分析

Q: 页框和页的定义分别是什么?
A: 页框是[[内存|主存]]的物理划分，页是进程的逻辑划分。

Q: 页框和页的区别是什么?
A: 页框是主存中实际存在的物理内存块，而页是进程逻辑地址空间的划分，并不一定对应实际的物理内存块。**可以类比酒店房间和预定房间的关系，页框是酒店房间，页是预定房间，预定房间不一定马上就能入住(分配到房间)。**

Q: 页框和页有什么联系?
A: 页表记录了页和页框之间的映射关系，通过页表可以将页映射到相应的页框。

Q: 页表项通常存储在哪里?
A: [[页表]]项通常存储在 [[进程控制块|PCB]] 中。

Q: 页表项的存储方式有哪些?
A: [[页表]]项的存储方式有两种：线性页表和多级页表。

Q: 线性页表和多级页表有什么区别?
A: 线性页表将所有页表项连续存储在一个线性地址空间中，而多级页表将页表项分层存储，例如二级页表将页表项分为多个页表，每个页表包含一部分页表项。

Q: 线性页表和多级页表各有什么优缺点?
A: 线性页表结构简单，但占用内存空间大，尤其是在地址空间很大的情况下；多级页表占用内存空间更小，但结构复杂，地址转换效率较低。**可以类比一本书的目录，线性页表像是一级目录，所有内容都在一个目录下，查找方便但目录会很长；多级页表像是有二级、三级目录，目录更简洁，但查找需要多翻几层。**

Q: 页面大小的选择会影响什么?
A: 页面大小的选择会影响内存利用率、地址转换效率和程序运行效率。

Q: 页面大小过大有什么缺点?
A: 页面大小过大，会导致内存利用率降低，因为每个页面都需要占用一个完整的页框，即使只使用了一部分空间，会产生较大的内部碎片。**例如，如果页面大小为 4KB，一个程序只需要 1KB 的内存，也需要占用一个完整的 4KB 页框，浪费了 3KB 的空间。**

Q: 页面大小过小有什么缺点?
A: 页面大小过小，会导致地址转换次数增加，因为需要更多的页表项来记录页面的映射关系，从而降低地址转换效率，页表也会占用更大的内存空间。

Q: 分页存储管理的优缺点是什么?
A: **优点**: 
    - 内存利用率高，可以减少外部碎片。
    - 地址空间扩展性强，每个进程都有独立的逻辑地址空间。
    - 方便进行内存共享和保护。
**缺点**: 
    - 页表占用内存空间。
    - 地址转换过程需要查表，降低了效率。

Q: 什么是页面置换算法?
A: 页面置换算法是指当内存不足时，选择将哪个页面换出到磁盘的算法。

Q: FIFO (先进先出) 页面置换算法是什么?
A: FIFO 算法淘汰最先进入内存的页面。**就像排队一样，先进入队列的人先出去。**

Q: [[LRU]] (最近最少使用) 页面置换算法是什么?
A: LRU 算法淘汰最近最少使用的页面。**就像最近最少使用的物品，更容易被遗忘或丢弃。**

Q: OPT (最佳置换) 页面置换算法是什么?
A: OPT 算法淘汰未来最长时间不会被访问的页面。**这是理论上的最佳算法，但在实际中难以实现，因为无法预知未来哪个页面会被访问。**

Q: 分页存储管理中存在外部碎片吗?
A: 不存在，分页存储管理中只存在内部碎片。

Q: 什么是内部碎片?
A: 内部碎片指的是每个页面分配的内存空间大于实际需要的内存空间，导致部分内存空间无法使用。**例如，如果页面大小为 4KB，一个程序只需要 1KB 的内存，也需要占用一个完整的 4KB 页框，浪费了 3KB 的空间。**

Q: 什么是外部碎片?
A: [[外部碎片]]指的是系统中存在一些空闲的内存空间，但这些空闲空间无法满足进程的内存需求，导致无法分配内存。**外部碎片在连续分配方式中比较常见，但在分页存储管理中不存在。**

Q: 有什么助记方法可以帮助记忆页框和页的区别?
A: “页框是主存的物理划分，页是进程的逻辑划分”。 
**可以联想：页框是物理存在的框架，页是逻辑上的页面。**

# 基本地址变换机构的anki卡片

## 基本地址变换机构

Q: 什么是页表寄存器（PTR）？
A: 页表寄存器（PTR）用于存储页表的起始地址 `F` 和页表长度 `M`。

Q: 页表寄存器（PTR）在地址变换过程中起什么作用？
A: 页表寄存器（PTR）在地址变换过程中提供页表的起始地址和长度，以便CPU能够根据逻辑地址找到对应的物理地址。
![](https://img.hwenyi.tech/202407291607798.webp)

Q: 基本地址变换机构的地址变换过程是怎样的？
A: 1. **计算页号和页内偏移**：根据逻辑地址确定页号 `P` 和页内偏移量 `W`。
2. **越界检查**：比较页号 `P` 和页表长度 `M`，检查是否越界(P >= M)。
3. **查询页表项**：使用页表寄存器中的页表起始地址 `F` 和页号 `P` 查询页表项，得到该页对应的块号。
4. **计算物理地址**：结合页表项中的内存块号和页内偏移量 `W`，得到物理地址。
5. **访问内存**：使用物理地址访问目标内存单元。
![](https://img.hwenyi.tech/202407291607799.webp)
![](https://img.hwenyi.tech/202407291607800.webp)

Q: 页号越界的情况是什么？
A: 页号 `P` 大于等于 页表长度 `M` 表示越界。
![](https://img.hwenyi.tech/202407291607798.webp)

Q: 页表项长度、页表长度和页面大小有什么区别？
A: - **页表项长度**：单个页表项占用的存储空间，例如：2B，4B。
- **页表长度**：页表项的总数，即总页数。
- **页面大小**：单个页面的存储空间，例如：4KB。
（主存中分为多个页面，这里指的是其中一个页面）。

Q: 如何手动模拟基本地址变换机构确定物理地址？
A: 通过给定的逻辑地址、页面大小和页表信息，手动模拟地址变换过程，计算出物理地址。例如，已知逻辑地址为 32768，页面大小为 4KB，页表中逻辑页号为 8 的页表项对应的块号为 5，则可以计算出物理地址为 5 * 4KB + 0 = 20KB。
![](https://img.hwenyi.tech/202407291607801.webp)

## 页表项大小探讨

Q: 为什么**页表项**大小通常设置为 2 的幂？
A: 为了简化页表的查询，通常将页表项大小设置为 2 的幂，确保每个页面可以恰好装下整数个页表项，避免空间浪费，方便地址计算。
![](https://img.hwenyi.tech/202407291607804.webp)

### 页表项大小与地址变换效率

Q: 页表项大小设置为2的幂次方，如何提高了地址变换的效率？
A: 页表项大小设置为2的幂次方后，可以通过简单的位运算快速计算出页表项在内存中的地址，从而加快地址变换的速度。例如，如果页表项大小为4B，则页表项的地址可以表示为页表起始地址 + 页号 * 4B，其中页号 * 4B 可以通过左移两位操作快速计算。

# 快表的anki卡片

## 快表

Q: 什么是快表(TLB, Translation Lookaside Buffer)?
A: 快表是一种高速缓存，存放最近访问的页表项副本，加速地址变换速度。 **补充说明:** 快表也称为联想寄存器，可以把它想象成页表的“快捷方式”，就像电脑桌面上的快捷方式一样，可以快速访问常用的程序。
![](https://img.hwenyi.tech/202407291607808.webp)

Q: 快表和内存中的页表(慢表)有什么区别？
A: 快表是高速缓存，访问速度比内存中的页表快很多。 **补充说明:** 快表就像一个小的“笔记本”，记录了最近常用的页表项，而内存中的页表就像一个大的“图书馆”，存放了所有的页表项。

### 快表与慢表比较

Q: 为什么快表不能存储整个页表？
A: 快表造价昂贵，容量有限。 **补充说明:** 可以想象一下，如果你的笔记本只能记几条笔记，你肯定只会记最重要的内容，而不会把整个图书馆的书都抄下来。

Q: 为什么要采用多级存储设备？
A: 平衡效率与成本。 **补充说明:** 就像我们生活中既有笔记本记录重要事项，也有图书馆存放大量书籍一样，计算机也需要不同级别的存储设备来满足不同的需求。

Q: 访问快表和访问内存的时间分别是多少？
A: 访问快表需要 1us，访问内存需要 100us。 **补充说明:** 这就像在笔记本上查找信息只需要几秒钟，而在图书馆查找信息可能需要几分钟甚至更长时间。

### 地址变换过程

Q: 引入快表后，地址变换过程有哪些步骤？
A: 1. CPU给出逻辑地址，硬件计算页号和页内偏移量。 
2. 将页号与快表中的页号进行比较。 
3. 若快表命中，直接获取内存块号，拼接物理地址，一次访存。 
4. 若快表未命中，访问内存页表，获取内存块号，拼接物理地址，两次访存。
**补充说明:** 这就像先在笔记本上查找信息，如果找到了就直接使用，如果找不到再去图书馆查找。

Q: 快表命中和未命中分别需要多少次访存？
A: 快表命中需要一次访存，快表未命中需要两次访存。 **补充说明:** 记住口诀：**命中一次，未命中两次**。

### 快表更新与替换

Q: 快表未命中时，找到页表项后，如何更新快表？
A: 将找到的页表项存入快表。 **补充说明:** 这就像把新学到的重要知识点记到笔记本上。

Q: 当快表已满时，如何替换旧的页表项？
A: 按照一定的算法替换，例如 LRU(最近最少使用)算法、FIFO(先进先出)算法等。 **补充说明:** LRU 算法就像我们平时整理笔记，把最近不常用的笔记放到一边，把常用的笔记放在手边。

### 局部性原理

Q: 为什么快表能够提升系统性能？
A: 由于局部性原理，程序访问的页表项往往具有重复性，快表可以缓存最近访问的页表项，提高命中率，减少访存次数。 **补充说明:** 这就像我们经常翻阅的笔记更容易记住一样，程序经常访问的页表项也更容易被缓存到快表中。

Q: 什么是时间局部性？
A: 如果执行了程序中的某条指令，那么不久后这条指令很有可能再次执行。 **补充说明:** 这就像我们背单词，重复记忆更容易记住。

Q: 什么是空间局部性？
A: 一旦程序访问了某个存储单元，在不久之后，其附近的存储单元也很有可能被访问。 **补充说明:** 这就像我们看书，通常会按顺序阅读，而不是跳来跳去。

### 查询案例分析

Q: 假设快表命中率为 90%，访问快表需要 1us，访问内存需要 100us，分析不同情况下访问一个逻辑地址所需的时间？
A: **补充说明:** 通过比较可以看出，使用快表可以显著减少访问时间。
  
| 方式           | 访问时间                                            |     |
| ------------ | ----------------------------------------------- | --- |
| 先查快表，不命中后查慢表 | `(1+100) * 0.9 + (1 + 100 + 100) * 0.1 = 111us` |     |
| 快表与慢表同时查询    | `(1+100) * 0.9 + (100 + 100) * 0.1 = 110.9us`   |     |
| 未采用快表        | 100 + 100 = 200us                               |     |

### 快表与Cache区别

Q: 快表和普通 Cache 有什么区别？
A: 快表存放页表项副本，而普通 Cache 存放各种数据副本。 
**补充说明:** 快表是专门为地址转换服务的，而普通 Cache 则可以缓存各种数据，例如指令、数据等。

### 快表的工作原理

Q: 快表是如何利用地址映射表来加速地址转换的？
A: 快表存储最近访问的页表项副本，可以直接根据页号查找对应的页表项，避免访问内存中的页表。
**补充说明:** 这就像在笔记本上查找信息，如果找到了就直接使用，不需要再去图书馆查找。

### 快表的设计与实现

Q: 快表的硬件结构是如何设计的？
A: 快表通常使用联想存储器来实现，可以根据页号快速查找对应的页表项。
**补充说明:** 联想存储器可以并行查找多个页号，从而提高查找速度。

### 快表与其他相关概念的区别

Q: 快表与普通Cache、页表有什么区别？
A: 快表存放页表项副本，普通 Cache 存放各种数据副本；
页表是存储在内存中的数据结构，用于记录虚拟地址到物理地址的映射关系。
**补充说明:** 它们都是为了提高系统性能而设计的，但应用场景和实现方式不同。

==页面大小==指的是一个==内存块==

# 两级页表知识点的anki卡片

## 单级页表的问题

Q: 单级页表会带来哪些问题？
A: 单级页表存在两个主要问题：
1. **页表必须连续存放**，占用大量**连续页框**，导致内存空间浪费。
2. 整个**页表常驻内存**，而进程只需访问少量页面即可运行，造成资源浪费。
牢记一点，页表是内存里每个块（页框）的索引，页表本身放在PCB里，PCB是在内存里的
![](https://img.hwenyi.tech/202407291607822.webp)

Q: 一个32位逻辑地址，页面大小4KB，页表项长度4B的系统，单级页表最多需要多少个页表项，最大需要占用多少内存空间，需要占用多少个页框？
A: 最多需要2^20个页表项 (因为页号占20位)，最大需要占用2^22 B (2^20个页表项 * 4B/页表项)内存空间，需要占用2^10个页框 (2^22 B / 2^12 B/页框)。
![](https://img.hwenyi.tech/202407291607816.webp)
**补充说明：可以想象一个巨大的图书馆，所有的图书索引都必须连续存放，这将占据巨大的空间，并且很多索引可能根本用不到。

### 问题 1 的解决方案：页表分页

Q: 如何解决单级页表中页表必须连续存放的问题？
A: 通过将页表分页，建立一级页表（页目录表），允许页表离散存放，减少连续页框需求。 就像将进程进行分页来解决进程需要连续存放的问题一样。

### 问题 2 的解决方案：虚拟存储技术

Q: 如何解决进程运行仅需部分页面，无需整个页表常驻内存的问题？
A: 使用虚拟存储技术，在页表项中增加标志位（存在位/驻留位），标记页面是否在内存中，并在需要时通过缺页中断调入。 这就好比我们看书，只需要把当前章节的内容加载到内存中，而不是把整本书都加载进来。
![](https://img.hwenyi.tech/202407291607824.webp)

## 二级页表概念

Q: 什么是二级页表？
A: 为离散分配的页表再建立一张页表，称为页目录表（外层页表、顶层页表），解决页表连续存放问题。可以理解为：页表的页表。

### 多级页表机制

Q: 为什么需要多级页表？
A: 为了满足各个页表的大小不能超过一个页面的要求，可能需要多级页表。
**细节点 1**：若是采用多级页表机制，则**各个页表的大小不能超过一个页面**
![](https://img.hwenyi.tech/202407291607825.webp)
首先**页面大小指的是一个内存块**：4KB = 212B，那么页面偏移位数为 12 位。
由于各个页表的大小不能超过一个页面，那么最大一个页表就是一个页表项大小也就是 4KB，又一个页表项为 4B，那么一个页表中有 4KB/4B = 1024 = 210，那么页号就是占据 10 位。
此时我们看下剩余逻辑地址位数：40 - 10 -12 = 18，那么按照常理我们会觉得剩余 18 位就是 1 级页号，不过还是有问题的，注意这个细节点：**各个页表的大小不能超过一个页面**。
那么我们需要多加一级页表，那么就有 3 级页表，1-3 级分别为：8、10、10。
![](https://img.hwenyi.tech/202407291607826.webp)

Q: 如何确定各级页表的页号位数？
A: 首先，页面大小指的是一个内存块：4KB = 2^12B，那么页面偏移位数为 12 位。由于各个页表的大小不能超过一个页面，那么最大一个页表就是一个页表项大小也就是 4KB，又一个页表项为 4B，那么一个页表中有 4KB/4B = 1024 = 2^10，那么页号就是占据 10 位。此时我们看下剩余逻辑地址位数：40 - 10 -12 = 18，那么按照常理我们会觉得剩余 18 位就是 1 级页号，不过还是有问题的，注意这个细节点：**各个页表的大小不能超过一个页面**。那么我们需要多加一级页表，那么就有 3 级页表，1-3 级分别为：8、10、10。
![](https://img.hwenyi.tech/202407291607826.webp)

### 二级页表与快表机构的关系

Q: 二级页表与快表机构有什么关系？
A: 快表机构可以加速二级页表的地址变换过程：
    - **快表：** 快表是一个高速缓存，用于存储最近使用的页表项，减少访问内存的次数。
    - **加速地址变换：** 当访问一个页面时，先查询快表，如果命中，则直接得到物理地址，否则再查询二级页表。
    由于二级页表需要多次访问内存，快表机构可以缓存常用的页表项，从而减少访存次数，提高地址变换效率。

## 二级页表地址变换

Q: 二级页表如何实现地址变换？
A: 二级页表地址变换过程如下：
    - 按照地址结构将逻辑地址拆分为一级页号、二级页号、页内偏移量。
    - 从PCB读出页目录表始址，根据一级页号查页目录表，找到二级页表位置。
    - 使用二级页号查询二级页表，确定物理地址块号。
    - 最终物理地址 = 物理地址块号 * 页大小 + 页内偏移量。
    例如：逻辑地址为 1000H，页目录表始址为 2000H，一级页号为 1，二级页号为 2，页内偏移量为 0，则物理地址为 (2000H + 1 * 4B) -> (3000H + 2 * 4B) -> 4000H + 0 = 4000H。
![](https://img.hwenyi.tech/202407291607822.webp)

Q: 各级页表的大小不能超过什么？
A: 一个页面 如果超过一个页面，就失去了分页的意义

### 访存次数分析

Q: 单级页表和两级页表在访存次数上有什么区别？
A: 单级页表两次访存，两级页表三次访存。
    单级页表只需要访问一次页表即可得到物理地址，而二级页表需要访问两次页表。

Q: 两级页表访存次数分析（假设没有快表机构）
A: 对于两级页表分析：①第一次访存（内存中的页目录表，一级页表）。②第二次访存（访问内存的二级页表）。③第三次访存：访问目标内存单元。

# 分段存储管理知识点

## 1.5.2.1 什么是分段

Q: 分段存储管理中，进程的地址空间是如何划分的？
A: 进程的地址空间按照程序自身的逻辑关系划分为若干个段，每个段都有一个段名（在低级语言中，程序员使用段名来编程），每段从 0 开始编址。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，每个段的起始地址是多少？
A: 每个段的起始地址都是 0。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，程序员如何使用段？
A: 程序员使用段名（通常是函数名）来编程。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，内存分配是以什么为单位进行的？
A: 内存分配以段为单位进行分配，每个段在内存中占据连续空间，但各个段之间可以不相邻。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，每个段在内存中占据的空间是怎样的？
A: 每个段在内存中占据连续空间，但各个段之间可以不相邻。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，逻辑地址结构由哪两部分组成？
A: 逻辑地址结构由段号（段名）和段内地址（段内偏移量）组成。
![](https://img.hwenyi.tech/202407291607830.webp)

Q: 分段存储管理中，段号的位数决定了什么？
A: 段号的位数决定了每个进程最多可以分几个段。
![](https://img.hwenyi.tech/202407291607829.webp)

Q: 分段存储管理中，段内地址位数决定了什么？
A: 段内地址位数决定了每个段的最大长度是多少。
![](https://img.hwenyi.tech/202407291607832.webp)

## 1.5.2.2 什么是段表

Q: 分段存储管理中，段表的作用是什么？
A: 段表建立了逻辑段（段号）到物理地址（基址）的映射关系。
![](https://img.hwenyi.tech/202407291607832.webp)

Q: 分段存储管理中，段表项中记录了什么信息？
A: 段表项中记录了该段在内存中的起始位置（基址）和段的长度。
![](https://img.hwenyi.tech/202407291607832.webp)

Q: 分段存储管理中，各个段表项的长度是否相同？
A: 是的，各个段表项的长度是相同的。
![](https://img.hwenyi.tech/202407291607832.webp)

Q: 分段存储管理中，如何计算段表项的容量？
A: 段表项的容量 = 段长位数 + 基址位数。
![](https://img.hwenyi.tech/202407291607832.webp)
举例：某系统按照字节寻址，采用分段存储管理，逻辑地址结构为（段号 16 位，段内地址 16 位），因此用 16 位即可表示最大段长，若是物理内存大小为 4GB，那么 32 位表示整个物理地址空间（基址）。那么**每个段表项的容量为 16+32 = 48 位 = 6B。**
由于段表项长度相同，因此段号可以是隐含的，不占存储空间。
若是段表存放的起始地址（基址）为 M，那么 K 号段对应的段表项存放位置为（在内存中）：M + K * 6，这里是找指定的段表在内存中的位置，根据段表号来查询。

Q: 分段存储管理中，如何根据段号找到段表项在内存中的位置？
A: 若段表存放的起始地址（基址）为 M，那么 K 号段对应的段表项存放位置为 M + K * 段表项长度。
![](https://img.hwenyi.tech/202407291607832.webp)

## 1.5.2.3 分段存储管理的地址变换

Q: 分段存储管理中，地址变换流程是怎样的？
A: 1. 从逻辑地址中取出段号。
2. 根据段号找到段表中的对应段表项。
3. 将段内地址与段表项中的段长进行比较，若段内地址 >= 段长，则发生越界中断。
4. 将段内地址与段表项中的基址相加，得到最终的物理地址。
![](https://img.hwenyi.tech/202407291607835.webp)

Q: 分段存储管理和分页存储管理的地址变换的主要区别是什么？
A: 分段地址变换需要检查**段内地址是否越界**，而分页地址变换不需要。

## 1.5.2.4 分段、分页对比

Q: 分段存储管理和分页存储管理中，页和段分别是什么单位？
A: 页是信息的**物理单位**，段是信息的**逻辑单位**。
**1、页是信息的物理单位**。分页的主要目的是实现离散分配，提高内存利用率。分页仅仅是系统管理上的需要，完全是系统行为，对用户不可见。
**2、段是信息的逻辑单位**。分段的主要目的是为了更好地满足用户需求。一个段通常包含着一组属于一个逻辑模块的信息。跟段是对用户可见的，用户编程时需要显式的给出段名。

Q: 分段存储管理和分页存储管理中，页和段对用户是否可见？
A: 页对用户不可见，段对用户可见。

Q: 分段存储管理和分页存储管理中，页和段的大小是否固定？
A: **页的大小固定，由系统决定**；**段的大小不固定，由用户程序决定**。

Q: 分段存储管理和分页存储管理的用户进程地址空间分别是几维的？
A: ①分页的用户进程地址空间是一维的，程序员只需给出一个**记忆符**即可表示一个地址。
![](https://img.hwenyi.tech/202407291607836.webp)
- 可以使用一个记忆符 A 来表示某个页面中某一个内存单元。
②分段的用户进程地址空间是二维的，程序员在标识一个地址时，**既要给出段名，也要给出段内地址**。
![](https://img.hwenyi.tech/202407291607837.webp)

Q: 分段存储管理和分页存储管理中，哪种方式更容易实现信息的共享与保护？
A: 分段更容易实现信息的共享与保护。
多个进程指向的段号只要有同样的段表项即可，两个段表项指向相同的位置。
![](https://img.hwenyi.tech/202407291607838.webp)

Q:为什么分页中不太能够实现信息的共享？
A:分页由于一个页框是固定大小的，可能会出现一个页中包含多个段的内容，若是像段一样让某个页表项指向这个页面，那么显得不太合理，其中有一部分是不允许被共享的。
![](https://img.hwenyi.tech/202407291607839.webp)
我们看下对应段表与分页的表：
![](https://img.hwenyi.tech/202407291607840.webp)
可以看到若是我们想要一个函数能够都被某个进程访问，由于我们是根据页来进行分长度的，每个页相同容量，此时就可能一个分页里有一部分函数 A 和另一个部分函数 B：
![](https://img.hwenyi.tech/202407291607841.webp)
这也是导致分页很难实现共享保护的问题。

Q: 分段存储管理和分页存储管理中，什么样的代码是可共享的？
A: "纯代码" 和 "可重入代码" 是可共享的。

Q: 分段存储管理和分页存储管理中，访问逻辑地址需要几次访存？
A: 都需要两次访存。
`分页（单级页表）`：第一次访存是查内存中的页表，第二次访存是访问目标内内存单元。总共两次访存。
`分段`：第一次访存是查内存中的段表，第二次访存访问目标内存单元。总共两次访存。
与分页系统类似，分段系统中也可以引入快表机构，将近期访问的段表项放入到快表中，这样可以少一次访问，加快地址变换速度。

### 分段与分页的对比总结

Q: 简述分段和分页的主要区别？
A: 分段是逻辑单位，面向用户，长度可变，更容易共享和保护；分页是物理单位，对用户透明，长度固定，更利于内存利用率。

# 段页式存储管理知识点

## 段页式管理方式

Q: 段页式管理方式中，每个进程需要几个段表？
A: 一个。一个进程对应一个段表，就像一个人的身份信息只有一张身份证一样。
![](https://img.hwenyi.tech/202407291607846.webp)
一个进程对应一个段表，但是一个进程可能会对应多个页表

Q: 段页式管理方式中，每个进程可能需要几个页表？
A: 多个。一个进程可能对应多个页表，就像一个人可能有多个银行账户一样。
![](https://img.hwenyi.tech/202407291607846.webp)

## 段页式管理的逻辑地址结构

Q: 段页式管理的逻辑地址结构由哪几部分组成？
A: 段号、页号、页内偏移量。
可以联想成地址：省（段号）- 市（页号）- 街道门牌号（页内偏移量）。
![](https://img.hwenyi.tech/202407291607847.webp)

页内偏移量决定了==页面（页面即是内存块）和内存块的大小==。例如，如果页内偏移量占 12 位，那么页面和内存块的大小为 2^12 = 4096 字节 (4KB)。

Q: 段页式管理的地址结构是几维的？
A: 二维。段页式管理的地址结构是二维的，需要段号和页号才能确定地址，就像确定一个房间需要楼层号和房间号。
而页式管理的地址结构是一维的，只需要页号就能确定地址，就像平房只需要房间号就能确定房间。
![](https://img.hwenyi.tech/202407291607848.webp)

## 段表和页表

Q: 段表项包含哪几部分内容？
A: 段号、段长、页表存放地址。
![](https://img.hwenyi.tech/202407291607848.webp)

## 段页式逻辑地址转换过程

Q: 通过段表可以获取什么？
A: 页表存放地址。通过段表可以获取页表存放地址，就像通过邮政编码可以找到城市的具体位置。
![](https://img.hwenyi.tech/202407291607848.webp)

Q: 使用什么可以减少访存次数至一次？
A: 快表 (TLB)。快表就像一个缓存，可以快速找到最近访问过的地址，从而减少访存次数。

