---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: 2024-11-17 07:56
updated: 2024-11-17 07:56
TARGET DECK: 刷题::25计组-王道::第 3 章 存储系统::3.6 虚拟存储器::anki
---
## 虚拟存储器的基本概念

Q: 虚拟存储器由哪些部件组成？
A: 虚拟存储器由主存和辅存共同组成。
主存的访问速度快，但容量较小且价格昂贵；
辅存的访问速度慢，但容量较大且价格便宜。

Q: 虚拟存储器对哪些程序员透明？
A: 虚拟存储器对应用程序员透明，这意味着应用程序员无需关心程序的实际物理地址，而只需要使用逻辑地址即可。

Q: 虚拟存储器具有哪些特点？
A: 虚拟存储器具有以下特点：
- 逻辑容量大：虚拟存储器的地址空间可以比实际物理内存大得多。
- 访问速度快：虚拟存储器利用局部性原理，将经常访问的数据或指令存储在主存中，从而提高访问速度。
- 成本低：虚拟存储器利用辅存来扩展主存空间，从而降低了存储系统的成本。

Q: 虚拟存储器是如何形成庞大地址空间的？
A: 虚拟存储器通过将主存和辅存的地址空间统一编址来形成庞大的地址空间。
操作系统负责将逻辑地址转换为物理地址，并将数据在主存和辅存之间进行调度。

Q: 用户编程时允许涉及的地址称为什么？
A: 用户编程时允许涉及的地址称为**虚地址**或**逻辑地址**。

Q: 虚地址对应的存储空间称为什么？
A: 虚地址对应的存储空间称为**虚拟空间**或**逻辑地址空间**。

Q: 实际的主存单元地址称为什么？
A: 实际的主存单元地址称为**实地址**或**物理地址**。

Q: 实地址对应的存储空间称为什么？
A: 实地址对应的存储空间称为**主存空间**或**物理地址空间**。

Q: 虚地址和实地址的大小关系？
A: 虚地址可以比实地址大很多。
这是因为虚拟存储器可以利用辅存来扩展主存空间，使得程序可以使用比实际物理内存更大的地址空间。

Q: CPU 如何使用虚地址？
A: 当 CPU 使用虚地址时，会先查找**快表 (TLB)**。
如果在快表中找到对应的页表项，则直接进行地址转换；
否则，CPU 会访问主存中的**页表**。
果页表项的**有效位**为 1，则表示该页面已经加载到主存中，CPU 可以直接访问；
否则，会发生**缺页异常**，操作系统会将所需的页面从辅存加载到主存中。

## 页面替换策略

Q: 虚拟存储器采用什么页面替换策略？
A: 虚拟存储器可以采用多种页面替换策略，例如 **FIFO (先进先出)**、**LRU (最近最少使用)**、**OPT (最佳替换)** 等。

Q: FIFO 算法的原理是什么？
A: FIFO 算法将最先进入内存的页面替换出去。

Q: LRU 算法的原理是什么？
A: LRU 算法将最近最少使用的页面替换出去。

Q: OPT 算法的原理是什么？
A: OPT 算法将未来最长时间内不会被访问的页面替换出去。OPT 算法是一种理想化的算法，在实际系统中难以实现。

Q: 为什么虚拟存储器通常采用 LRU 算法？
A: LRU 算法的性能通常比 FIFO 算法更好，因为它更符合程序的局部性原理。

## 页式虚拟存储器

Q: 页式虚拟存储器以什么为基本单位？
A: 页式虚拟存储器以**页**为基本单位。页是虚拟存储器和主存之间进行数据交换的单位。

Q: 主存空间中的页称为什么？
A: 主存空间中的页称为**物理页**、**实页**或**页框**。

Q: 虚拟地址空间中的页称为什么？
A: 虚拟地址空间中的页称为**虚拟页**或**虚页**。

### 页表

Q: 页表的作用是什么？
A: 页表用于记录虚拟页和物理页之间的映射关系。每个进程都有一个页表，用于记录该进程的虚拟地址空间中每个页面对应的物理页框号。

Q: 页表一般保存在哪里？
A: 页表一般保存在主存中。

Q: 页表项中包含哪些信息？
A: 页表项中通常包含以下信息：
- **有效位**: 表示该页面是否已经加载到主存中。
- **物理页号**: 表示该页面对应的物理页框号。
- **访问权限**: 表示该页面的访问权限，例如只读、读写等。
- **修改位**: 表示该页面是否已经被修改。
- **引用位**: 表示该页面是否被访问过。

Q: 页表项中的有效位有什么作用？
A: 页表项中的有效位用于判断该页面是否已经加载到主存中。如果有效位为 1，则表示该页面已经加载到主存中，CPU 可以直接访问；否则，会发生缺页异常。

Q: 页表项中的修改位有什么作用？
A: 页表项中的修改位用于判断该页面是否已经被修改。如果修改位为 1，则表示该页面已经被修改，当该页面被替换出去时，需要将修改后的内容写回辅存；否则，不需要写回辅存。

Q: 页表项中的引用位有什么作用？
A: 页表项中的引用位用于判断该页面是否被访问过。引用位可以用于页面替换算法，例如 LRU 算法。

### 缺页异常

Q: 什么是缺页异常？
A: 当 CPU 访问的页面不在主存中时，会发生缺页异常。缺页异常是一种中断，操作系统会捕获该中断，并执行缺页异常处理程序。

Q: 缺页异常处理程序如何处理缺页？
A: 缺页异常处理程序会执行以下步骤：
1. 查找空闲的物理页框。
2. 如果没有空闲的物理页框，则选择一个页面进行替换。
3. 将所需的页面从辅存加载到主存中。
4. 更新页表。
5. 重新执行导致缺页异常的指令。

### 地址转换

Q: 虚拟地址分为哪两个字段？
A: 虚拟地址分为**虚页号**和**页内偏移地址**两个字段。虚页号用于查找页表，页内偏移地址用于确定数据在页面中的位置。

Q: 物理地址分为哪两个字段？
A: 物理地址分为**物理页号**和**页内偏移地址**两个字段。物理页号用于确定数据所在的物理页框，页内偏移地址用于确定数据在物理页框中的位置。

Q: 页内偏移地址在虚拟地址和物理地址中是否相等？
A: 是的，页内偏移地址在虚拟地址和物理地址中是相等的。这是因为页面大小是固定的，虚拟页和物理页的大小相同。

Q: 虚拟地址到物理地址的转换是如何实现的？
A: 虚拟地址到物理地址的转换过程如下：
1. CPU 将虚拟地址中的虚页号作为索引，在页表中查找对应的页表项。
2. 如果页表项的有效位为 1，则取出页表项中的物理页号，并将物理页号与虚拟地址中的页内偏移地址拼接，得到物理地址。
3. 如果页表项的有效位为 0，则发生缺页异常。

### 快表 (TLB)

Q: 快表用什么实现？
A: 快表通常用 SRAM 实现，因为 SRAM 的访问速度比 DRAM 快得多。

Q: 快表的工作原理类似于什么？
A: 快表的工作原理类似于 Cache，都是利用局部性原理来提高访问速度。

Q: 快表通常采用什么映射方式？
A: 快表通常采用全相联或组相联映射方式。

Q: 快表的表项由什么组成？
A: 快表的表项由**虚拟页号**、**物理页号**和其他一些控制位组成。

Q: 全相联映射下，TLB 如何工作？
A: 在全相联映射方式下，TLB 中的每个表项都可以存储任何虚拟页号对应的页表项。
当 CPU 访问一个虚拟地址时，TLB 会将该虚拟地址的虚页号与 TLB 中所有表项的虚拟页号进行比较。
如果找到匹配的表项，则直接取出对应的物理页号；否则，发生 TLB 缺失。

Q: 组相联映射下，TLB 如何工作？
A: 在组相联映射方式下，TLB 被分成若干个组，每个组可以存储若干个页表项。当 CPU 访问一个虚拟地址时，TLB 会根据该虚拟地址的虚页号计算出对应的组号，然后在该组中查找匹配的页表项。如果找到匹配的表项，则直接取出对应的物理页号；否则，发生 TLB 缺失。

### 具有 TLB 和 Cache 的多级存储系统

Q: 在具有 TLB 和 Cache 的多级存储系统中，CPU 访存过程中存在哪三种缺失情况？
A: 在具有 TLB 和 Cache 的多级存储系统中，CPU 访存过程中存在三种缺失情况：
- **TLB 缺失**: 要访问的页面的页表项不在 TLB 中。
- **Cache 缺失**: 要访问的主存块不在 Cache 中。
- **缺页**: 要访问的页面不在主存中。

Q: 缺页时，TLB 是否也必然缺失？
A: 是的，缺页时，TLB 也必然缺失。这是因为 TLB 存储的是页表的一部分副本，如果页面不在主存中，那么 TLB 中也不会有该页面的页表项。

Q: 缺页时，Cache 是否也必然缺失？
A: 是的，缺页时，Cache 也必然缺失。这是因为 Cache 存储的是主存的一部分副本，如果页面不在主存中，那么 Cache 中也不会有该页面的数据。

Q: Cache 缺失处理由什么完成？
A: Cache 缺失处理由硬件完成。当发生 Cache 缺失时，Cache 控制器会自动从主存中读取所需的数据，并将其加载到 Cache 中。

Q: 缺页处理由什么完成？
A: 缺页处理由操作系统完成。当发生缺页异常时，操作系统会执行缺页异常处理程序，将所需的页面从辅存加载到主存中。

Q: TLB 缺失可以用什么来处理？
A: TLB 缺失既可以用硬件处理，也可以用软件处理。

Q: 硬件处理 TLB 缺失的优点是什么？
A: 硬件处理 TLB 缺失的速度更快。

Q: 软件处理 TLB 缺失的优点是什么？
A: 软件处理 TLB 缺失的成本更低，并且更灵活。

Q: 在具有 TLB 和 Cache 的多级存储系统中，CPU 一次访存操作可能涉及哪些存储器的访问？
A: 在具有 TLB 和 Cache 的多级存储系统中，CPU 一次访存操作可能涉及以下存储器的访问：
1. CPU 首先访问 TLB。
2. 如果 TLB 命中，则直接取出物理页号，并访问 Cache。
3. 如果 TLB 缺失，则访问主存中的页表。
4. 如果页表命中，则取出物理页号，并访问 Cache。
5. 如果页表缺失，则发生缺页异常，操作系统将所需的页面从辅存加载到主存中。
6. 如果 Cache 命中，则直接取出数据。
7. 如果 Cache 缺失，则从主存中读取数据，并将其加载到 Cache 中。

## 段式虚拟存储器

Q: 段式虚拟存储器中的段是如何划分的？
A: 段式虚拟存储器中的段是按照程序的逻辑结构划分的。例如，一个程序可以分为代码段、数据段、堆栈段等。每个段都有自己的名称和长度。

Q: 各个段的长度是否相同？
A: 不相同。各个段的长度可以根据程序的需要而有所不同。

Q: 虚拟地址到实地址之间的变换是如何实现的？
A: 虚拟地址到实地址之间的变换是由**段表**实现的。段表存储了每个段的起始地址和长度。

Q: 段表是什么？
A: 段表是操作系统维护的一个数据结构，用于记录每个段的起始地址和长度。

Q: 段表中的每一行记录什么信息？
A: 段表中的每一行记录一个段的信息，包括：
- **段号**: 用于标识该段。
- **段基址**: 该段在主存中的起始地址。
- **段限长**: 该段的长度。

Q: 为什么段表中要给出各段的起始地址与段的长度？
A: 因为段的长度是可变的，所以需要记录每个段的起始地址和长度，以便进行地址转换。

Q: 段式虚拟存储器对程序员是否透明？
A: 段式虚拟存储器对程序员是不透明的。程序员需要知道段号才能访问数据。

Q: 段式虚拟存储器的优点是什么？
A: 段式虚拟存储器的优点包括：
- **方便编程**: 程序员可以按照程序的逻辑结构来划分段，使得程序更易于理解和维护。
- **方便共享**: 不同的进程可以共享同一个段，从而节省内存空间。
- **方便保护**: 可以为每个段设置不同的访问权限，从而保护程序的安全性。

Q: 段式虚拟存储器的缺点是什么？
A: 段式虚拟存储器的缺点包括：
- **内存碎片**: 由于段的长度是可变的，所以容易产生内存碎片，降低内存利用率。
- **地址转换开销**: 地址转换需要访问段表，增加了地址转换的开销。

## 段页式虚拟存储器

Q: 段页式虚拟存储器是如何组织程序的？
A: 段页式虚拟存储器结合了段式和页式的优点。它首先将程序按照逻辑结构划分为若干个段，然后将每个段再划分为若干个固定大小的页。

Q: 段页式虚拟存储器以什么为基本交换单位？
A: 段页式虚拟存储器以**页**为基本交换单位。

Q: 虚地址分为哪三部分？
A: 在段页式虚拟存储器中，虚地址分为三部分：
- **段号**: 用于标识该虚拟地址所在的段。
- **页号**: 用于标识该虚拟地址所在的页。
- **页内偏移地址**: 用于确定数据在页面中的位置。

Q: 段页式虚拟存储器的地址变换过程？
A: 段页式虚拟存储器的地址变换过程如下：
1. CPU 首先根据段号访问段表，得到该段的页表起始地址。
2. 然后根据页号访问页表，得到该页的物理页框号。
3. 最后将物理页框号与页内偏移地址拼接，得到物理地址。

Q: 段页式虚拟存储器的优点是什么？
A: 段页式虚拟存储器的优点包括：
- **兼具段式和页式的优点**: 既可以方便编程和共享，又可以减少内存碎片。
- **提高内存利用率**: 页的大小是固定的，可以减少内存碎片。
- **方便保护**: 可以为每个段设置不同的访问权限，从而保护程序的安全性。

Q: 段页式虚拟存储器的缺点是什么？
A: 段页式虚拟存储器的缺点包括：
- **地址转换开销**: 地址转换需要访问段表和页表，增加了地址转换的开销。

## 虚拟存储器与 Cache 的比较

Q: 虚拟存储器与 Cache 的基本交换单位是什么？
A: 虚拟存储器与 Cache 的基本交换单位都是**块**。虚拟存储器以**页面**为单位进行数据交换，Cache 以**Cache 行**为单位进行数据交换。

Q: 虚拟存储器与 Cache 都存在哪些问题？
A: 虚拟存储器与 Cache 都存在以下问题：
- **地址映射**: 如何将逻辑地址转换为物理地址。
- **块替换**: 当缓存空间不足时，如何选择要替换的块。
- **一致性维护**: 如何保证缓存中的数据与主存中的数据一致。

虚拟存储器与 Cache 都依据==局部性原理==。局部性原理是指程序在执行过程中，倾向于访问最近访问过的数据或指令，以及这些数据或指令附近的其他数据或指令。

### 不同之处

Q: 虚拟存储器由什么实现？
A: 虚拟存储器由操作系统和硬件共同实现。

Q: Cache 对程序员是否透明？
A: Cache 对程序员是透明的。

Q: 虚拟存储器对程序员是否透明？
A: 虚拟存储器对应用程序员是透明的，对系统程序员是不透明的。

Q: Cache 缺失和缺页的处理开销哪个更大？
A: 缺页的处理开销更大。这是因为缺页需要访问辅存 (例如磁盘)，而 Cache 缺失只需要访问主存。辅存的访问速度比主存慢得多。
