---
publish: true
tags: []
aliases: 
finished: true
title: anki
created: "2024-11-18 05:46"
updated: "2024-11-18 13:47"
TARGET DECK: 刷题::25计网-王道::第 2 章 物理层::2.2 传输介质::anki
---
### 传输介质及分类

Q: 传输介质与物理层的关系是什么？
A: 传输介质在物理层的下面，物理层规定了电气特性，能够识别所传送的比特流。

#### 传输介质的分类

Q: 传输介质的分类有哪些？
A: - 导向性传输介质：电磁波被导向沿着固体媒介（铜线 / 光纤）传播。
- 非导向性传输介质：自由空间，介质可以是空气、真空、海水等。

### 导向性传输介质

#### 双绞线

Q: 双绞线的定义是什么？
A: 双绞线由两根采用一定规则并排绞合的、相互绝缘的铜导线组成。

Q: 双绞线的组成部分有哪些？
A: - 铜线：两根导线，相互绞合在一起。
- 绝缘层：在绞合的铜线外面套上一层绝缘层。
- 聚氯乙烯套层：是 PVC 材料，就是一个塑料套管。

Q: 双绞线绞合的作用是什么？
A: 绞合可以减少对相邻导线的电磁干扰。

Q: 双绞线的类型有哪些？
A: - 屏蔽双绞线 (STP)：在双绞线的外面加上一层金属丝编织成的屏蔽层，抗电磁干扰能力强。
- 非屏蔽双绞线 (UTP)：没有屏蔽层，抗电磁干扰能力弱。

Q: 双绞线的特点是什么？
A: - 价格便宜
- 模拟传输和数字传输都可使用
- 通信距离一般为几公里 - 数十公里

#### 同轴电缆

Q: 同轴电缆的结构是什么？
A: 同轴电缆由导体铜质芯线、绝缘层、网状编织屏蔽层和塑料外层构成。

Q: 同轴电缆的类型有哪些？
A: - ${50\Omega }$ 同轴电缆：主要用于传送基带数字信号。
- ${75\Omega }$ 同轴电缆：主要用于传送宽带信息。

Q: 同轴电缆的特点是什么？
A: - 抗干扰性比双绞线好
- 传输距离更远
- 价格较双绞线更贵

#### 光纤

Q: 光纤通信的原理是什么？
A: 利用光导纤维传递光脉冲来进行通信，有光脉冲表示 1，无光脉冲表示 0。

Q: 光纤的结构是什么？
A: 光纤主要由纤芯和包层构成，纤芯很细，直径仅为 $8 \sim  {100\mu }\mathrm{m}$，包层较纤芯有较低的折射率，光波通过纤芯进行传导。

Q: 光纤的类型有哪些？
A: - 多模光纤：光纤的直径较大，光线在纤芯中会产生多次反射，适合近距离传输。
- 单模光纤：光纤的直径很细，光线在纤芯中不会产生多次反射，适合远距离传输。

Q: 光纤的特点是什么？
A: - 通信容量非常大
- 抗雷电和电磁干扰性能好
- 传输损耗小，中继距离长
- 无串音干扰，保密性好
- 体积小，重量轻

#### 光纤的组成

Q: 光纤的组成部分有哪些？
A: - 纤芯：光波在纤芯中传导。
- 包层：包层较纤芯有较低的折射率，光波通过纤芯进行传导。

Q: 光纤是如何实现光电转换的？
A: - 发送端：使用发光二极管或半导体激光器将电脉冲转换为光脉冲。
- 接收端：使用光电二极管将光脉冲还原为电脉冲。

#### 光纤的分类

Q: 光纤的分类有哪些？
A: - 多模光纤：光纤的直径较大，光线在纤芯中会产生多次反射，适合近距离传输。
- 单模光纤：光纤的直径很细，光线在纤芯中不会产生多次反射，适合远距离传输。

#### 光纤的特点

Q: 光纤的特点是什么？
A: - 传输损耗小，中继距离长
- 抗雷电和电磁干扰性能好
- 无串音干扰，保密性好
- 体积小，重量轻

### 非导向性传输介质

#### 非导向性传输介质的必要性

Q: 为什么需要非导向性传输介质？
A: 非导向性传输介质可以实现无线通信，方便用户随时随地进行通信。

#### 常考的非导向性传输介质

Q: 常考的非导向性传输介质（无线传输介质）有哪些？
A: - 无线电波
- 微波
- 红外线 / 激光

#### 无线电波

Q: 无线电波的特点是什么？
A: - 信号可以向所有方向传播。
- 具有较强的穿透能力。
- 可以传输很长的距离。

Q: 无线电波的优点是什么？
A: 接收设备无需对应某个方向，简化了通信连接。

#### 微波

Q: 微波的特点是什么？
A: - 频率较高，频段范围宽，数据率很高。
- 信号固定方向传播。

Q: 微波通信的应用场景有哪些？
A: - 地面微波接力通信
- 卫星通信

Q: 地面微波接力通信的原理是什么？
A: 利用多个中继站，每个中继站可以朝向指定的下一个中继站发出信号，然后不断循环，最终来完成地球上地面上的接力通信过程。

Q: 卫星通信的原理是什么？
A: 利用地球同步卫星作为中继来转发微波信号，可以克服地面微波通信距离的限制。

Q: 微波通信的优点是什么？
A: - 通信容量大
- 距离远
- 范围广
- 光波通信和多址通信

Q: 微波通信的缺点是什么？
A: - 传播时延长
- 受气候影响大
- 误码率较高
- 成本高

#### 红外线和激光

Q: 红外线和激光的特点是什么？
A: - 信号固定方向传播。
- 需要在发送方和接收方之间有一条视线通路。

Q: 红外线和激光的区别是什么？
A: - 红外线和激光将要传输的信号分别转换为各自的信号格式，即红外光信号和激光信号，再在空间中传播。
- 微波不需要转格式，而红外线和激光需要转格式。

### 物理层接口的特性

#### 物理层接口特性的定义

Q: 物理层接口特性的定义是什么？
A: 物理层接口特性是指与传输介质的接口有关的一些特性，用于屏蔽各种传输介质之间的差异，使数据链路层只需考虑如何完成本层的协议和服务。

#### 物理层接口的特性

Q: 物理层接口的特性有哪些？
A: 1. 机械特性：指明接口所用接线器的形状和尺寸、引脚数目和排列、固定和锁定装置等。
2. 电气特性：指明在接口电缆的各条线上的电压范围、传输速率和距离限制等。
3. 功能特性：指明某条线上出现的某一电平的电压的意义，以及每条线的功能。
4. 过程特性：指明对不同功能的各种可能事件的出现顺序。

#### 机械特性

Q: 物理层接口的特性的机械特性的定义是什么？
A: 机械特性指明接口所用接线器的形状和尺寸、引脚数目和排列、固定和锁定装置等。

#### 电气特性

Q: 物理层接口的特性的电气特性的定义是什么？
A: 电气特性指明在接口电缆的各条线上的电压范围、传输速率和距离限制等。

#### 功能特性

Q: 物理层接口的特性的功能特性的定义是什么？
A: 功能特性指明某条线上出现的某一电平的电压的意义，以及每条线的功能。

#### 过程特性

Q: 物理层接口的特性的过程特性的定义是什么？
A: 过程特性指明对不同功能的各种可能事件的出现顺序。

#### 物理层接口特性的作用

Q: 物理层接口特性的作用是什么？
A: 物理层接口特性屏蔽了各种传输介质之间的差异，使数据链路层只需考虑如何完成本层的协议和服务。
