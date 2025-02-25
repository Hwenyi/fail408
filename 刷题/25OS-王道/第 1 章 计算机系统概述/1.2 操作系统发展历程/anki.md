---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: 2024-11-06 07:22
updated: 2024-11-06 07:22
TARGET DECK: 刷题::25OS-王道::第 1 章 计算机系统概述::1.2 操作系统发展历程::anki
---

## 手工操作阶段

Q:手工操作阶段用户在计算机上进行计算需要做什么？
A:用户需要人工干预所有工作，例如程序的装入、运行和结果输出等。

Q:手工操作阶段有什么缺点？
A:①用户独占全机，资源利用率低。
②CPU 等待手工操作，CPU 的利用不充分。

Q:手工操作阶段人机矛盾体现在哪里？
A:人机矛盾体现在程序执行速度和资源利用率上，手工操作速度慢，造成资源浪费。

Q:为什么手工操作阶段CPU的利用率低？
A:手工操作速度慢，CPU 需等待人工操作，导致 CPU 空闲时间长。

## 批处理阶段

### 单道批处理系统

Q:什么是单道批处理系统？
A:将一批作业以脱机方式输入磁带，并由监督程序控制，使这批作业能自动逐个运行，但内存中始终只有一道作业。

Q:单道批处理系统的主要特征是什么？
A:自动性、顺序性和单道性。

Q:单道批处理系统中，作业是如何输入到计算机的？
A:作业以脱机方式输入到磁带中，即事先将作业输入到磁带，再由计算机读取磁带上的作业信息。

Q:单道批处理系统中，监督程序的作用是什么？
A:监督程序负责控制作业的执行顺序，协调 CPU 和 I/O 设备之间的工作，自动完成作业的处理。

### 多道批处理系统

Q:什么是多道批处理系统？
A:允许多个作业同时进入内存，并在 CPU 的控制下交替运行，共享系统资源。

Q:多道批处理系统是如何实现CPU和I/O设备并行工作的？
A:当某道程序因请求 I/O 操作而暂停运行时，CPU 便立即转去运行另一道程序，这是通过中断机制实现的。

Q:多道程序设计的特点是什么？
A:多道、宏观上并行、微观上串行。

Q:多道程序设计中**多道**指的是什么？
A:计算机内存中同时存放多道相互独立的程序。

Q:多道程序设计中**宏观上并行**指的是什么？
A:同时进入系统的多道程序都处于运行过程中，但都未运行完毕。

Q:多道程序设计中**微观上串行**指的是什么？
A:内存中的多道程序轮流占有 CPU，交替执行。

Q:多道批处理操作系统的优点是什么？
A:资源利用率高、系统吞吐量大。

Q:多道批处理操作系统的缺点是什么？
A:用户响应的时间较长、不提供人机交互能力。

Q:多道批处理系统中，作业调度程序的作用是什么？
A:作业调度程序负责按照某种算法从外存的后备队列中选择若干个作业调入内存。

Q:多道批处理系统中，如何实现多道程序共享系统资源？
A:操作系统负责管理和分配系统中的各种资源，例如 CPU、内存、I/O 设备等，并为每个程序分配所需的资源，实现资源共享。

## 分时操作系统

Q:什么是分时技术？
A:将处理器的运行时间分成很短的时间片，按时间片轮流将处理器分配给各联机作业使用。

Q:分时技术是如何让用户感觉独占一台计算机的？
A:由于计算机速度很快，作业运行轮转得也很快，给每个用户的感觉就像是自己独占一台计算机。

Q:什么是分时操作系统？
A:允许多个用户通过终端同时共享一台主机，用户可以通过终端与主机交互操作。

Q:分时系统与多道批处理系统有什么不同？
A:分时系统实现了人机交互，用户可以实时控制程序运行；而多道批处理系统则以批处理方式执行作业，用户无法干预。

Q:分时系统的主要特征是什么？
A:同时性、交互性、独立性和及时性。

Q:分时系统中，时间片轮转法是如何工作的？
A:将 CPU 时间划分成若干个时间片，每个进程轮流占用一个时间片。

Q:分时系统中，如何实现用户与自己的作业进行交互？
A:用户通过终端向操作系统发出指令，操作系统接收并执行指令，再将结果返回给用户终端。

## 实时操作系统

Q:为什么会出现实时操作系统？
A:为了能在某个时间限制内完成某些紧急任务而不需要时间片排队。

Q:实时操作系统根据对时间限制的要求可以分为哪两种？
A:硬实时系统和软实时系统。

Q:硬实时系统和软实时系统的应用场景分别是什么？
A:硬实时系统：导弹控制系统、工业控制系统等，对截止时间要求严格。软实时系统：视频点播、网络游戏等，允许偶尔的延迟。

Q:实时操作系统的特点是什么？
A:及时性和可靠性。

Q:实时操作系统如何实现及时性？
A:通过高优先级调度算法和快速的任务切换机制，确保对外部事件的及时响应。

Q:实时操作系统如何实现可靠性？
A:通过冗余设计、错误检测和恢复机制，保证系统在出现故障时仍能正常运行。

## 网络操作系统

Q:什么是网络操作系统？
A:管理和控制计算机网络的系统软件，实现各台计算机之间的数据互相传送和资源共享。

Q:网络操作系统最主要的的特点是什么？
A:网络中各种资源的共享及各台计算机之间的通信。

Q:网络操作系统有哪些应用场景？
A:例如文件共享、打印机共享、数据库访问等，以及电子邮件、网络浏览等网络服务。

Q:网络操作系统如何实现网络中各种资源的共享？
A:网络操作系统通过文件服务器、打印服务器等方式提供对共享资源的访问。

Q:网络操作系统如何实现各台计算机之间的通信？
A:利用网络协议，例如 TCP/IP 协议，实现不同计算机之间的数据传输。

## 分布式计算机系统

Q:什么是分布式计算机系统？
A:由多台计算机组成，各计算机通过网络互联，共同完成任务，且用户共享所有资源。

Q:分布式计算机系统的特点是什么？
A:分布性和并行性。

Q:分布式操作系统与网络操作系统的本质区别是什么？
A:分布式操作系统强调多台计算机协同完成同一任务，而网络操作系统强调资源共享和通信。

Q:分布式计算机系统有哪些应用场景？
A:例如分布式数据库、云计算平台、并行计算等。

Q:分布式计算机系统如何实现分布性和并行性？
A:将任务分解成多个子任务，分配给不同的计算机并行执行，最终汇总结果。
