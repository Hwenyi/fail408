---
publish: true
tags: []
aliases: 
finished: true
title: anki
created: "2024-11-18 05:32"
updated: "2024-11-18 14:17"
TARGET DECK: 刷题::25计网-王道::第 4 章 网络层::4.3 IPV6::anki
---
### IPv6 的主要特点

#### 1. 更大的地址空间

Q: IPv6 的地址空间比 IPv4 大多少？
A: IPv6 的地址空间是 IPv4 的 ${2}^{96}$ 倍，IPv6 将地址从 IPv4 的 32 位增大到 128 位, IPv6 的地址空间是 IPv4 的 ${2}^ {{128} - {32}} = {2}^{96}$ 倍。

#### 3. 灵活的首部格式

Q: IPv6 的首部格式有什么不一样的特点？
A: IPv6 定义了许多可选的扩展首部，不仅可提供比 IPv4 更多的功能，而且能提高路由器的处理效率。

Q: 路由器如何处理 IPv6 的扩展首部？
A: 路由器对扩展首部不进行处理。

#### 4. 改进的选项

Q: IPv6 的选项有什么特点？
A: IPv6 首部长度是固定的，其选项放在有效载荷中，选项是灵活可变的。

Q: IPv4 的选项有什么特点？
A: IPv4 所规定的选项是固定不变的，其选项放在首部的可变部分。

#### 5. 允许协议继续扩充

Q: IPv6 和 IPv4 在协议扩充方面有什么区别？
A: IPv6 允许不断扩充功能，而 IPv4 的功能是固定不变的。

#### 6. 支持即插即用

Q: IPv6 如何实现即插即用？
A: IPv6 支持自动配置，因此不需要使用 DHCP。

#### 8. 分片机制

Q: IPv6 的分片机制有什么特点？
A: IPv6 只有源主机才能分片，是端到端的，不允许类似 IPv4 传输路径中的路由分片。

#### 9. 首部长度

Q: IPv6 和 IPv4 的首部长度有什么区别？
A: IPv6 首部长度是固定的 40 字节，而 IPv4 首部长度是可变的（必须是 4 字节的整数倍）。

#### 10. 增强的安全性

Q: IPv6 如何增强安全性？
A: 身份鉴别和保密功能是 IPv6 的扩展首部。

#### 兼容性

Q: IPv6 与 IPv4 兼容吗？
A: IPv6 与 IPv4 不兼容，但总体而言它与所有其他的互联网协议兼容，包括 TCP、UDP、ICMP、IGMP 和 DNS 等，只是在少数地方做了必要的修改（大部分是为了处理长地址）。

### ipv6数据报的基本首部

IPv6 数据报由==两部分==组成: ==基本首部==和==有效载荷== (也称净负荷)。有效载荷由==零个==或==多个扩展首部==（扩展首部不属于 IPv6 数据报的首部）及其后面的数据部分构成 
![](https://img.hwenyi.tech/202406021524376.webp)

因为取消了首部中不必要的功能, IPv6 基本首部的字段数减少到只有 ==8== 个, 但由于 IPv6 地址长度为 ==128== 位,所以 IPv6 基本首部的长度反而增大到 ==40B== 
![](https://img.hwenyi.tech/202406021524377.webp)

### IPv6 基本首部字段

#### 1. 版本

Q: ipv6基本首部中版本字段占多少位？
A: 4 位
![](https://img.hwenyi.tech/202406021524377.webp)

Q: ipv6基本首部中版本字段的值是多少？
A: 6 
![](https://img.hwenyi.tech/202406021524377.webp)

#### 2. 通信量类

Q: ipv6基本首部中通信量类字段占多少位？
A: 8 位 
![](https://img.hwenyi.tech/202406021524377.webp)

Q: 通信量类字段的作用是什么？
A: 用来区分不同的 IPv6 数据报的类别或优先级 
![](https://img.hwenyi.tech/202406021524377.webp)

#### 3. 流标号

Q: ipv6基本首部中流标号字段占多少位？
A: 20 位 
![](https://img.hwenyi.tech/202406021524377.webp)

Q: ipv6基本首部中流标号字段的作用是什么？
A: IPv6 提出流的抽象概念，流是指互联网上从特定源点到特定终点（单播或多播）的一系列数据报，而在这个“流”所经过的路径上的路由器都保证指明的服务质量。所有属于同一个流的数据报都具有相同的流标号 
![](https://img.hwenyi.tech/202406021524377.webp)

#### 4. 有效载荷长度

Q: ipv6基本首部中有效载荷长度字段占多少位？
A: 16 位 
![](https://img.hwenyi.tech/202406021524377.webp)
![](https://img.hwenyi.tech/202407071943261.webp)

Q: ipv6基本首部中有效载荷长度字段的作用是什么？
A: 指明 IPv6 数据报除基本首部以外的字节数（所有扩展首部都算在有效载荷之内）
![](https://img.hwenyi.tech/202406021524377.webp)

Q: ipv6基本首部中有效载荷长度字段的最大值是多少？
A: 65535 字节
![](https://img.hwenyi.tech/202406021524377.webp)

#### 5. 下一个首部

Q: ipv6基本首部中下一个首部字段占多少位？
A: 8 位
![](https://img.hwenyi.tech/202406021524377.webp)

Q: ipv6基本首部中下一个首部字段的作用是什么？
A: 当 IPv6 没有扩展首部时，其作用与 IPv4 的协议字段一样，它指明 IPv6 数据报所运载的数据是何种协议数据单元；当 IPv6 带有扩展首部时，它就标识后面第一个扩展首部的类型 
![](https://img.hwenyi.tech/202406021524377.webp)

#### 6. 跳数限制

Q: ipv6基本首部中跳数限制字段占多少位？
A: 8 位 
![](https://img.hwenyi.tech/202406021524377.webp)

Q: ipv6基本首部中跳数限制字段的作用是什么？
A: 类似于 IPv4 首部的 TTL 字段。源点在每个数据报发出时即设定某个限制值（最大为 255）。路由器每次转发时将其值减 1，减为零时就将该数据报丢弃。
![](https://img.hwenyi.tech/202406021524377.webp)

#### 7. 源地址和目的地址

Q: ipv6基本首部中源地址和目的地址字段占多少位？
A: 128 位。
![](https://img.hwenyi.tech/202406021524377.webp)

### IPv6 地址

#### IPv6 地址类型

Q: IPv6 数据报的目的地址有哪些类型？
A: 1. 单播
2. 多播
3. 任播
![](https://img.hwenyi.tech/202407062005680.webp)

Q: 为什么 IPv6 不使用 IPv4 的广播地址？  
A: 因为多播地址可以包括广播地址的功能。在 IPv4 中，广播地址用于发送数据包给同一个局域网中的所有节点。在 IPv6 中，可以使用多播地址来实现广播功能，将所有主机地址添加到一个多播组中，然后将数据包发送到这个多播组即可。

多播地址==只能==作为==目的地址==，不能作为==源地址==。

#### 任播地址

Q: IPv6 数据报的目的地址中的**任播地址**是什么？
A: 任播地址是 IPv6 增加的一种类型，任播的终点是一组计算机，但数据报只交付其中的一台计算机，通常是距离最近的一台计算机。
![](https://img.hwenyi.tech/202407071943268.webp)

ipv6 中任播地址==只能==作为==目的地址==。

Q: 请总结任播地址的特点和应用场景。  
A: 任播地址是 IPv6 的独有地址，它是一种一对多通信方式，但实质上还是一对一通信，只是表现形式好像是一个跟多个主机通信。任播地址只能作为目的地址，当 IP 数据包的目的地址是任播地址时，数据包会发送给任播组内离发送方最近的一台主机。任播地址可以用于将数据发送给最近的服务器或路由器。
![](https://img.hwenyi.tech/202407071943268.webp)

#### IPv6 地址表示法

Q: IPv6 地址如何表示？
A: [[ipv6]] 标准使用冒号十六进制记法，即把地址中的每 4 位用一个十六进制数表示，并用冒号分隔每 16 位。

Q: [[ipv6]] 地址如何缩写？
A: 1. 当 16 位域的开头有一些 0 时，可以采用一种缩写表示法，但在域中必须至少有一个数字。
2. 当有相继的 0 值域时，还可以进一步缩写。这些域可用双冒号缩写 $(::)$。当然，双冒号表示法在一个地址中仅能出现一次，因为0值域的个数没有编码，需要从指定的总的域的个数来推算。这样一来，前述地址可被更紧凑地书写成4BF5:BA5F:39A:A:2176。

#### IPv6 地址分类

Q: IPv6 地址有哪些分类？
A: 1. 未指明地址
2. 环回地址
3. 多播地址
4. 本地链路单播地址
5. 全球单播地址

#### 未指明地址

Q: IPv6 的地址分类中的未指明地址的作用是什么？
A: 该地址**不能**用作目的地址，只能用于还未配置 IPv6 地址的主机作为源地址。

#### 环回地址

Q: IPv6 的地址分类中的环回地址的作用是什么？
A: 该地址的作用与 IPv4 的环回地址相同，但 IPv6 的环回地址**仅此一个**。

#### 多播地址

Q: IPv6 的地址分类中的多播地址的作用是什么？
A: 该地址的作用和 IPv4 的一样。这类地址占 IPv6 地址空间的 **1/256**。

#### 本地链路单播地址

Q: IPv6 的地址分类中的本地链路单播地址的作用是什么？
A: 该地址的作用类似于 IPv4 的私有 IP 地址。

#### 全球单播地址

Q: IPv6 的地址分类中的全球单播地址的结构是什么？
A: 全球单播地址采用三级结构：
1. 全球路由选择前缀（48 比特）
2. 子网标识符（16 比特）
3. 接口标识符（64 比特）
![](https://img.hwenyi.tech/202407062010170.webp)
![](https://img.hwenyi.tech/202403271138566.webp)

Q: 全球单播地址中的**全球路由选择前缀**的作用是什么？
A: 用于互联网中的路由选择，相当于 IPv4 分类地址中的网络号。
![](https://img.hwenyi.tech/202407062010170.webp)
![](https://img.hwenyi.tech/202403271138566.webp)

Q: 全球单播地址中的**子网标识符**的作用是什么？
A: 用于各机构构建自己的子网。
![](https://img.hwenyi.tech/202407062010170.webp)
![](https://img.hwenyi.tech/202403271138566.webp)

Q: 全球单播地址中的**接口标识符**的作用是什么？
A: 用于指明主机或路由器的单个网络接口，相当于 IPv4 分类地址中的主机号。
![](https://img.hwenyi.tech/202407062010170.webp)

Q: IPv6 地址的接口标识符有什么特点？
A: IPv6 地址的接口标识符有 64 位之多，足以对各种接口的硬件地址直接进行编码。
![](https://img.hwenyi.tech/202407062010170.webp)
![](https://img.hwenyi.tech/202403271138566.webp)

Q: IPv6 如何利用接口标识符？
A: IPv6 可直接从 128 位地址的最后 64 位中直接提取出相应的硬件地址，而不需要使用地址解析协议 (ARP) 进行地址解析。
![](https://img.hwenyi.tech/202407062010170.webp)

### IPv4 向 IPv6 过渡策略

#### 1. 双协议栈

Q: 双协议栈是什么？
A: 双协议栈是指在一台设备上同时装有 IPv4 和 IPv6 两个协议栈，分别配置了一个 IPv4 地址和一个 IPv6 地址，因此这台设备既能和 IPv4 网络通信，又能和 IPv6 网络通信。

Q: 双协议栈主机如何选择使用 IPv4 还是 IPv6 地址？
A: 双协议栈主机使用应用层的域名系统 (DNS) 获知目的主机采用的是哪种地址。若 DNS 返回的是 IPv4 地址，则双协议的源主机就使用 IPv4 地址。若 DNS 返回的是 IPv6 地址，则双协议栈的源主机就使用 IPv6 地址。

#### 2. 隧道技术

Q: 隧道技术是什么？
A: 隧道技术是指在 IPv6 数据报要进入 IPv4 网络时，把整个 IPv6 数据报封装成 IPv4 数据报的数据部分，使原来的 IPv6 数据报就好像在 IPv4 网络的隧道中传输。当 IPv4 数据报离开 IPv4 网络时，再将其数据部分交给主机的 IPv6 协议。

### IPv6 数据报首部长度

#### 字段数量

IPv6将IPv4数据报首部中不必要的功能取消了，这使得IPv6数据报基本首部中的字段数量减少到==只有8个==

#### 首部长度

但由于IPv6地址的长度扩展到了128比特，因此使得IPv6数据报基本首部的长度反而增大到了==40字节==

#### 与 IPv4 首部长度对比

Q: IPv6 数据报基本首部的长度比 IPv4 数据报首部固定部分的长度增加了多少？
A: 20 字节。

Q: 为什么 IPv6 数据报基本首部长度比 IPv4 数据报首部固定部分的长度更长？
A: 虽然 IPv6 取消了 IPv4 数据报首部中不必要的功能，减少了字段数量，但由于 IPv6 地址的长度扩展到了 128 比特，因此使得 IPv6 数据报基本首部的长度反而增大了。

IPv6比IPv4数据报首部==固定部分的长度==（20字节）增大了==20字节==

### IPv6 首部变化

#### 1. 首部长度字段

Q: IPv6 首部为什么取消了首部长度字段？
A: 因为 IPv6 数据报的首部长度是固定的 40 字节。
![](https://img.hwenyi.tech/202403240947474.webp)

Q: IPv6 和 IPv4 的首部长度有什么区别，分别是多少的整数倍？
A: IPv6 首部长度必须是 8B 的整数倍，IPv4 首部是 4B 的整数倍。

#### 2. 区分服务字段

Q: IPv6 首部为什么取消了区分服务字段？
A: 因为 IPv6 数据报首部中的通信量类和流标号字段实现了区分服务字段的功能。
![](https://img.hwenyi.tech/202403240947777.webp)

Q: IPv6 和 IPv4 的服务类型字段有什么区别？  
A: IPv6 取消了服务类型字段。

#### 3. 总长度字段

Q: IPv6 首部为什么取消了总长度字段？
A: 因为 IPv6 数据报的首部长度是固定的 40 字节，只有其后面的有效载荷长度是可变的。
![](https://img.hwenyi.tech/202403240947174.webp)

Q: IPv6 和 IPv4 的总长度字段有什么区别？  
A: IPv6 取消了总长度字段，改用有效载荷长度字段。

#### 4. 标识、标志和片偏移字段

Q: IPv6 首部为什么取消了标识、标志和片偏移字段？
A: 因为这些功能已包含在 IPv6 数据报的分片扩展首部中。
![](https://img.hwenyi.tech/202403240948547.webp)

Q: IPv6 和 IPv4 的分片机制有什么区别？  
A: IPv6 只能在主机处分片，IPv4 则可以在路由器和主机处分片。

Q: IPv6 只能够在主机处分片，那若是在**传输的链路层时 MTU 最大传输单元规定很小**，但是当前的 IPv6 数据包很大，需要进行分片怎么办？
A: 此时就需要在路由器这里将它**丢弃掉，返回一个差错报告报文**，注意这里这里的差错报告报文是 ICMPv6 协议。

#### ICMP 协议

Q: IPv6 和 IPv4 的 ICMP 协议有什么区别？  
A: IPv6 使用 ICMPv6 协议，它包含了 IPv4 ICMP 协议中没有的报文类型，例如 "分组过大"。

ICMPv6：针对于上面链路层若是要求 MTU 大小范围 < 当前传输 IVP6 数据包大小，会附加报文类型 =="分组过大"==。

ICMPv6比ICMPv4要复杂得多，它合并了原来的==地址解析协议ARP==和==网际组管理协议IGMP==的功能。因此与IPv6配套使用的网际层协议就==只有==ICMPv6这一个协议。

#### 5. 生存时间 TTL 字段

Q: IPv6 首部为什么把生存时间 TTL 字段改称为跳数限制字段？
A: 这样名称与作用更加一致。
![](https://img.hwenyi.tech/202403240948137.webp)

#### 6. 协议字段

Q: IPv6 首部为什么取消了协议字段？
A: 改用下一个首部字段。
![](https://img.hwenyi.tech/202403240948207.webp)

#### 7. 首部检验和字段

Q: IPv6 首部为什么取消了首部检验和字段？
A: 这样可以加快路由器处理 IPv6 数据报的速度。
![](https://img.hwenyi.tech/202403240949884.webp)

#### 8. 选项字段

Q: IPv6 首部为什么取消了选项字段？
A: 改用扩展首部来实现选项功能，路由器通常不对扩展首部进行检查，大大提高了路由器的处理效率。
![](https://img.hwenyi.tech/202403240949195.webp)

