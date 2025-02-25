---
publish: true
tags: 
aliases: 
finished: true
TARGET DECK: 刷题::25OS-王道::第 5 章 IO 管理::5.2 设备独立性软件::anki
title: anki
created: 2024-11-16 05:11
updated: 2024-11-16 12:22
---
## 2.1 IO 核心子系统

### 2.1.1 I/O 系统概述

Q: 什么是 I/O 系统？它包含哪些部分？
A: I/O 系统（I/O 子系统）属于操作系统的内核部分，主要包含设备独立性软件、设备驱动程序、中断处理程序。
![](https://img.hwenyi.tech/202408061431782.webp)

### 2.1.2 用户层软件和设备独立性软件层的功能

Q: 用户层软件在 I/O 系统中主要实现了什么功能？
A: 假脱机技术（SPOOLing 技术）。
![](https://img.hwenyi.tech/202408061430017.webp)

Q: 设备独立性软件在 I/O 系统中主要实现了哪些功能？
A: I/O 调度、设备保护、设备分配与回收、缓冲区管理（即缓冲与高速缓存）。
![](https://img.hwenyi.tech/202408061430017.webp)

#### 1. I/O 调度

Q: 什么是 I/O 调度？
A: I/O 调度是指当多个 I/O 请求到来时，使用某种调度算法确定满足 I/O 请求的顺序。

Q: 常用的磁盘调度算法有哪些？
A: 先来先服务算法、最短寻道优先算法、SCAN 算法、C-SCAN 算法，LOCK 算法、C-LOCK 算法。

Q: 其他设备的 I/O 调度可以使用哪些算法？
A: 先来先服务算法、优先级算法、短作业优先算法。

#### 2. 设备保护

Q: I/O 系统如何实现设备保护？
A: I/O 系统将设备看作特殊的文件，为每个设备建立一个文件控制块 (FCB)，并根据 FCB 记录的信息来判断用户是否有相应的访问权限。

### 知识总览

Q: I/O 核心子系统要实现的功能有哪些？
A: ![](https://img.hwenyi.tech/202411161311110.webp)
- 假脱机技术（SPOOLing 技术）
- I/O 调度
- 设备保护
- 设备分配与回收
- 缓冲区管理

## 2.2 假脱机技术（SPOOLing 技术，用户层软件层）

### 2.2.1 脱机技术的发展

Q: 什么是脱机技术？
A: 脱机技术是指在主机之外进行输入/输出操作，**不占用主机时间，由外围控制机完成**。
![](https://img.hwenyi.tech/202408061429926.webp)

Q: 脱机技术的好处是什么？
A: ![](https://img.hwenyi.tech/202408061429926.webp)
- 缓解了 CPU 和慢速 I/O 设备的速度矛盾。
- 提高了 CPU 的利用率。
- 允许 CPU 在忙碌时提前进行输入/输出操作。

### 2.2.2 假脱机技术

Q: 什么是假脱机技术？
A: 假脱机技术（SPOOLing 技术）是使用软件方式模拟脱机技术，通过磁盘缓冲区来实现。
![](https://img.hwenyi.tech/202408061429926.webp)

### 2.2.3 假脱机技术的实现原理

Q: 假脱机技术使用了哪些机制来模拟脱机技术？
A: ![](https://img.hwenyi.tech/202408061429927.webp)
- 输入井和输出井：模拟脱机输入/输出时的磁带，用于存放 I/O 数据。
- 输入进程和输出进程：模拟外围控制机，负责将数据在设备、缓冲区和磁盘之间进行传输。
- 输入/输出缓冲区：暂存输入/输出数据，作为数据中转站。
- 井管理程序

Q: 输入井和输出井的作用是什么？  
A: ![](https://img.hwenyi.tech/202408061429928.webp)
- 输入井：用于存放从输入设备读取的数据。
    - 模拟脱机输入时的磁带，用于收容 I/O 设备输入的数据。
- 输出井：用于存放要输出到输出设备的数据。
    - 模拟脱机输出时的磁带，用于收容用户进程输出的数据。
![](https://img.hwenyi.tech/202408061429929.webp)

Q: 输入进程和输出进程的作用是什么？  
A:![](https://img.hwenyi.tech/202408061429930.webp)
- 输入进程：将数据从输入设备传送到输入缓冲区，再存放到输入井。
- 输出进程：将数据从内存传送到输出井，再从输出井传送到输出设备。
`输入进程`：来实现的输入进程就是模拟脱机。
`输出进程`：是模拟脱机输出时的外围控制机。
![](https://img.hwenyi.tech/202408061429929.webp)

Q: 输入缓冲区和输出缓冲区的作用是什么？  
A:![](https://img.hwenyi.tech/202408061429931.webp)
- 输入缓冲区：用于暂存从输入设备读取的数据，再传送到输入井。
- 输出缓冲区：用于暂存从输出井读取的数据，再传送到输出设备。
![](https://img.hwenyi.tech/202408061429932.webp)

Q: 井管理程序的作用是什么？  
A: 用于控制作业与磁盘井之间信息的交换。

### 2.2.4 共享打印机的原理

Q: 什么是独占设备和共享设备？
A: - `独占式设备`：只允许各个进程串行使用的设备，一段时间内只能满足一个进程的请求。
- `共享设备`：允许多个进程 "同时" 使用的设备（宏观上同时使用，微观上可能是交替使用）。可以同时满足多个进程的使用请求。

Q: 如何使用假脱机技术实现共享打印机？
A: ![](https://img.hwenyi.tech/202408061429933.webp)
1. SPOOLing 系统在输出井中为每个打印请求分配一个缓冲区，并将要打印的数据写入缓冲区。
2. SPOOLing 系统为每个打印请求建立一个打印请求表，并将其加入到等待队列。
3. 当打印机空闲时，SPOOLing 系统从等待队列中取出队首请求，并将数据从输出井传送到打印机机进行打印。
![](https://img.hwenyi.tech/202408061429934.webp)

Q: 假脱机技术如何实现打印机的共享？
A: 每个进程在提出打印请求时，系统都会在输出井中为其分配一个存储区，相当于分配了一个逻辑设备，让每个进程都觉得自己在独占一台打印机，从而实现对打印机的共享。

## 2.3 设备的分配与回收

### 2.3.1 设备分配时考虑的因素

Q: 设备分配时需要考虑哪些因素？
A: ![](https://img.hwenyi.tech/202408061429937.webp)
- 设备的固有属性
- 设备分配算法
- 设备分配的安全性

#### 1. 设备的固有属性

Q: 设备的固有属性可以分为哪三种？
A: 
- `独占设备`：一个时间段只能够分配给一个进程（如打印机）。
- `共享设备`：可同时分配给多个进程使用（如磁盘），实际上各进程往往是宏观上同时共享使用设备，而微观上交替执行。
- `虚拟设备`：采用 SPOOLing 技术将独占设备改造成虚拟的共享设备，可同时分配给多个进程使用。（如 SPOOLing 技术实现的共享打印机）

#### 2. 设备分配算法

Q: 设备分配常用的算法有哪些？
A: 
- 先来先服务
- 优先级高者优先
- 短任务优先

#### 3. 设备分配的安全性

Q: 设备分配的两种方式是什么？它们各有什么优缺点？
A: 
- 安全分配方式：进程获得设备后便阻塞，不能再请求其他资源。
    - 优点：不会发生死锁。
    - 缺点：CPU 和 I/O 设备只能串行工作。
- 不安全分配方式：进程发出 I/O 请求后仍继续运行，可以同时请求多个设备。
    - 优点：进程推进迅速。
    - 缺点：有可能发生死锁。

### 2.3.2 静态分配与动态分配

Q: 什么是静态分配？
A: 进程运行前为其分配全部所需资源，运行结束后归还资源。

Q: 什么是动态分配？
A: 进程运行过程中动态申请设备资源。

### 2.3.3 设备分配管理中的数据结构

Q: 设备、控制器和通道之间是什么关系？
A: 树形关系，一个通道可以控制多个控制器，每个控制器可以控制多个设备。
![](https://img.hwenyi.tech/202408061429938.webp)

Q: 设备分配管理中使用了哪些数据结构？
A: ![](https://img.hwenyi.tech/202408061429938.webp)
- 设备控制表 (DCT)
- 控制器控制表 (COCT)
- 通道控制表 (CHCT)
- 系统设备表 (SDT)

#### 1. 设备控制表 (DCT)

Q: 设备控制表 (DCT) 包含哪些字段？
A: ![](https://img.hwenyi.tech/202408061429939.webp)
设备控制表（DCT）`包含的属性有：设备类型、设备标识符、设备状态、指向控制器表的指针、重复执行次数或时间、设备队列的队首指针。
`设备类型`：如打印机 / 扫描仪 / 键盘。
`设备标识符`：即物理设备名，系统中的每个设备的物理设备名唯一。
`设备状态`：忙碌 / 空闲 / 故障…
`指向控制器表的指针`：每个设备由一个控制器控制，该指针可找到相应控制器的信息。
`重复执行次数时间`：主要是用于记录失败了几次。只有当重复执行多次 I/O 操作后仍然不成功，才认为此次 I/O 失败。
- 对于使用打印机有时候会卡纸的现象，并不是执行一次操作失败就会认为真的失败了，系统会重复执行多次。
`设备队列的队首指针`：指向正在等待该设备的进程队列（由进程 PCB 组成队列）。
- 若是此时进程正在等待某一个 I/O 设别的分配，此时这个 I/O 设备暂时无法分配给它时，那么这个进程就会挂到对应的 I/O 设备控制表所指向的这个等待队列的队尾，这个队列指针实际上指向的就是对应的阻塞队列。
**注**：“进程管理 "章节中曾经提到过" 系统会根据阻塞原因不同，将进程 PCB 挂在到不同的阻塞队列当中去”。

#### 2. 控制器控制表 (COCT)

Q: 控制器控制表 (COCT) 包含哪些字段？
A: ![](https://img.hwenyi.tech/202408061429940.webp)
控制器控制表（COCT)`：每个设备控制器都会对应一张 COCT。操作系统根据 COCT 的信息对控制器进行操作和管理。
- `控制器标识符`：各个控制器的唯一 ID。
- `控制器状态`：忙碌 / 空闲 / 故障…
- `指向通道表的指针`：每个控制器由一个通道控制，该指针可找到相应通道的信息。
- `控制器队列的队首指针、控制器队列的队尾指针`：指向正在等待该控制器的进程队列（由进程 PCB 组成队列）。

#### 3. 通道控制表 (CHCT)

Q: 通道控制表 (CHCT) 包含哪些字段？
A: ![](https://img.hwenyi.tech/202408061429941.webp)
通道控制表（CHCT）`：每个通道都会对应一张 CHCT。操作系统根据 CHCT 的信息对通道进行操作和管理。
- 通道标识符：各个通道的唯一 ID。
- 通道状态：忙碌 / 空闲 / 故障…
- 与通道连接的控制器表首址：可通过该指针找到该通道管理的所有控制器相关信息（COCT）。
- 通道队列的队首指针、通道队列的队尾指针：指向正在等待该通道的进程队列（由进程 PCB 组成队列）。
若是通道暂时不能为一个进程该服务，那么进程依然需要等待这个通道的服务。最后两个字段是指向等待这个通道的进程队列。

#### 4. 系统设备表 (SDT)

Q: 系统设备表 (SDT) 包含哪些信息？
A: 系统设备表（SDT）`：记录了系统中全部设备的情况，每个设备对应一个表目。
![](https://img.hwenyi.tech/202408061429942.webp)
在这个表中包含多条设备，每条设备记录中都包含了设备情况，各个字段如下信息：
- 设备类型：例如打印机 / 扫描仪 / 键盘。
- 设备标识符：唯一物理设备名。
- DCT（设备控制表）：这个设备的信息数据的地址。
- 驱动程序入口：该设备程序的入口地址。

### 2.3.4 设备分配的步骤

Q: 设备分配的步骤有哪些？
A: ![](https://img.hwenyi.tech/202408061429943.webp)
1. 根据设备名查找系统设备表 (SDT)。
2. 检查设备状态，若空闲则分配设备，否则将进程加入设备队列。
3. 分配控制器，若空闲则分配，否则将进程加入控制器队列。
4. 分配通道，若空闲则分配，否则将进程加入通道队列。

### 2.3.5 设备分配步骤的改进

Q: 设备分配步骤有哪些缺点？
A: - 用户编程时必须使用物理设备名。
- 更换物理设备后程序无法运行。
- 进程请求的物理设备忙碌时，即使有其他同类型空闲设备，进程也需要阻塞等待。
例如三台打印机：若是其中一台 A 被占用，此时又有用户想要请求，此时会进入到阻塞中，哪怕其他类型的计算机，但是还是不能够进行使用。

Q: 如何改进设备分配步骤？
A: 建立逻辑设备与物理设备名的映射机制，用户编程时**只需要提供逻辑设备名**。
![](https://img.hwenyi.tech/202408061429949.webp)
实际精简：就是将一开始使用物理设备名改进为使用逻辑设备名来找即可，匹配得到 SDT 的一个表目后将其添加到逻辑设备表 LUT 中新增加一个表项，之后都是一模一样！

Q: 什么是逻辑设备表 (LUT)？
A: 逻辑设备表 (LUT) 建立了逻辑设备名与物理设备名之间的映射关系，方便操作系统根据逻辑设备名找到对应的物理设备和驱动程序。
![](https://img.hwenyi.tech/202408061429948.webp)

Q: 逻辑设备表 (LUT) 的作用是什么？  
A: 用于将逻辑设备名映射为物理设备名。

Q: 逻辑设备表 (LUT) 包含哪些内容？  
A: 逻辑设备名、物理设备名和设备驱动程序的入口地址。

## 2.4 缓冲区管理

### 2.4.1 什么是缓冲区？

Q: 什么是缓冲区？
A: 缓冲区是一个存储区域，可以由专门的硬件寄存器组成，也可以利用内存作为缓冲区。

#### 1. 磁盘高速缓存 (Disk Cache)

Q: 磁盘高速缓存的作用是什么？  
A: 磁盘高速缓存利用内存中的存储空间来暂存从磁盘中读出的一系列盘块中的信息，以提高磁盘的 I/O 速度。

Q: 磁盘高速缓存的两种形式是什么？  
A: - 在内存中开辟一个单独的空间作为缓存区，大小固定。
- 将未利用的内存空间作为一个缓冲池，供请求分页系统和磁盘 I/O 时共享。

### 2.4.2 缓冲区的作用

Q: 缓冲区的作用是什么？
A: ![](https://img.hwenyi.tech/202408061429952.webp)
1. 缓和 CPU 与 I/O 设备之间速度不匹配的矛盾。
2. 减少对 CPU 的中断频率，放宽对 CPU 中断响应时间的限制。
3. 解决数据粒度不匹配的问题。
4. 提高 CPU 与 I/O 设备之间的并行性。
![](https://img.hwenyi.tech/202408061429953.webp)
![](https://img.hwenyi.tech/202408061429954.webp)

Q: 缓冲区的实现方法有哪些？  
A: - 采用硬件缓冲器。
- 利用内存作为缓冲区。

### 2.4.3 单缓冲

Q: 什么是单缓冲？
A: 单缓冲是指操作系统在主存中为用户进程分配一个缓冲区，用于暂存输入/输出数据。
![](https://img.hwenyi.tech/202408061429958.webp)

Q: 单缓冲的工作原理是什么？
A: ![](https://img.hwenyi.tech/202408061429958.webp)
1. I/O 设备将数据输入到缓冲区。
2. 缓冲区满后，数据被传送到用户进程工作区。
3. 用户进程处理数据。
4. 用户进程将数据输出到缓冲区。
5. 缓冲区空后，I/O 设备可以继续输入数据。

Q:单缓冲每处理一块数据平均需要多长时间？
A:`结论，单缓冲的平均时间 = max {T, C} + M`
**情况 1：假设初始状态为工作区满，缓冲区空，T>C**
![](https://img.hwenyi.tech/202408061429959.webp)
由于 C 时间短，那么我们先来执行 C，由于初始状态工作区满，那么我们需要耗费 C 时间来进行处理，与此同时块设备也可以并行执行输入操作时长为 T。
**注意**：由于缓冲区的规则，**只有缓冲区填满之后才能够执行传输操作**，所以必须等待 T 时间结束之后才能够进行传送操作执行 M 时间。
- 加粗的部分就是下面时序图的 C、T，让填充区满必须执行完 T 时间才能够去执行 M 操作。
![](https://img.hwenyi.tech/202408061429960.webp)
那么之后的执行操作基本都是一致的，每次都是执行 T+M 时间，那么平均用时即为 `T+M`：
![](https://img.hwenyi.tech/202408061429961.webp)
**情况 2：假设初始状态为工作区满，缓冲区空，T<C**
此时我们可以先执行输入操作花费 T 时间，对应 CPU 处理用户进程的工作区也需要 C 时间，两者可以并行的完成。
由于 T 时间短，所以输入操作会先执行完，此时缓冲区已满，但是注意此时还不能够执行传送操作，因为在用户进程的工作区里数据还没有被处理完，此时需要等待处理 C 全部完成之后，才可以进行传送操作，对应的时序图如下图所示：
![](https://img.hwenyi.tech/202408061429962.webp)
那么之后的操作同理，所以平均用时为：`C+M`
![](https://img.hwenyi.tech/202408061429963.webp)

Q: 单缓冲的优缺点是什么？
A: - 优点：实现简单。
- 缺点：效率较低，CPU 和 I/O 设备的并行性不高。

### 2.4.4 双缓冲

Q: 什么是双缓冲？
A: 双缓冲是指操作系统在主存中为用户进程分配两个缓冲区，用于提高 I/O 效率。
![](https://img.hwenyi.tech/202408061429964.webp)

Q: 双缓冲的工作原理是什么？
A: ![](https://img.hwenyi.tech/202408061429964.webp)
1. I/O 设备将数据输入到一个缓冲区，同时 CPU 可以从另一个缓冲区读取数据。
2. 当一个缓冲区满时，I/O 设备可以切换到另一个缓冲区继续输入数据。

Q:双缓冲区每处理一块数据平均需要多长时间？
A:**结论**：采用双缓冲策略，无论是`T>m+c`还是`T<C+M`处理一个数据块的平均耗时为`Max(T，C+M)`
**情况 1：假设初始状态为工作区空，其中一个缓冲区满，另一个缓冲区空，假设 T>C+M**
![](https://img.hwenyi.tech/202408061429965.webp)
- 初始时，缓冲区 1 满，缓冲区 2 空，用户进程工作区为空。
我们可以执行`缓冲区1->工作区2`传送 (M)，与此同时可以并行完成`块设备—>内存的输入`(T)，在这个过程里若是传送操作完成可以立马开始执行处理 © 操作，所以最终的时序图如下图所示：
![](https://img.hwenyi.tech/202408061429966.webp)
当一次数据传输完毕之后，此时只有当 T 输入完成之后，我们的缓冲区才会有填满一块数据，所以我们需要再 T 执行完之后才能够执行传送 (M)，后面的流程与第一个流程类似：
![](https://img.hwenyi.tech/202408061429967.webp)
那么此时处理一块数据平均用时 = `T` 时间。
**情况 2：假设初始状态为工作区空，其中一个缓冲区满，另一个缓冲区空，假设 T<C+M**
同样对于`缓冲区1—>工作区` 与 `块设备—>缓冲区2` 可以并行执行，对于对于处理操作实际可以连带着在传送 (M) 完成之后执行，那么第一轮操作如下图所示：
![](https://img.hwenyi.tech/202408061429968.webp)
图中可以看到处理 © 操作阶段，我们是无法将缓冲区 1 或者 2 中的数据来传输到工作区的，因为当前工作区并没有被处理完，所以只能够等待处理 © 结束之后才能够继续完成传送 (M) 操作。
此时当 T 执行完成之后，可以继续完成 设备—> 缓冲区 1 中写入数据，在处理 © 没有执行完的过程中不能够执行传送的操作，此时可以发现之后的第二次、第三次它们就不再有规律，如下图所示：
![](https://img.hwenyi.tech/202408061429969.webp)
但是根据图示还是能够很清晰的看到每一轮花费的时间都是`M+C`，这个也就是平均时间。

Q: 双缓冲的优缺点是什么？
A: 
- 优点：提高了设备和 CPU 的并行程度，效率比单缓冲高。
- 缺点：当输入输出速度相差很大时，效果不理想。

### 2.4.5 循环缓冲

Q: 什么是循环缓冲？
A: 循环缓冲是指将多个大小相等的缓冲区链接成一个循环队列，通过 in 和 out 指针来管理缓冲区的输入和输出。

### 2.4.6 缓冲池

Q: 什么是缓冲池？
A: [[缓冲池]]是由系统中共用的缓冲区组成，并通过空缓冲队列、输入队列、输出队列和四个工作缓冲区来管理这些缓冲区。
![](https://img.hwenyi.tech/202408061429972.webp)

Q: 缓冲池的四种工作缓冲区是什么？
A: ![](https://img.hwenyi.tech/202408061429973.webp)
- hin：用于收容输入数据的工作缓冲区。
- sin：用于提取输入数据的工作缓冲区。
- hout：用于收容输出数据的工作缓冲区。
- sout：用于提取输出数据的工作缓冲区。
![](https://img.hwenyi.tech/202408061429974.webp)
![](https://img.hwenyi.tech/202408061429975.webp)
![](https://img.hwenyi.tech/202408061429976.webp)

