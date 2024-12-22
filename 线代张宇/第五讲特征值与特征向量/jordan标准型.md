---
publish: true
tags: []
aliases: 
finished: true
title: jordan标准型
created: "2024-10-15 09:04"
updated: "2024-10-20 10:37"
---
https://www.bilibili.com/video/BV1DG4y187pS?t=1089.8

![](https://img.hwenyi.live/202411301329899.webp)

![](https://img.hwenyi.live/202411301329118.webp)

![](https://img.hwenyi.live/202411301329058.webp)

![](https://img.hwenyi.live/202411301329063.webp)

![](https://img.hwenyi.live/202410151737844.webp)

在复习用书、模拟卷中，经常会出现形如

$$
\begin{bmatrix} a & 1 \\ & a \end{bmatrix}, \quad
\begin{bmatrix} a & 1 & \\ & a & \\ & & a \end{bmatrix}, \quad
\begin{bmatrix} a & & \\ & a & 1 \\ & & b \end{bmatrix}
$$

的矩阵，特征是在对角线上方或下方出现若干个 1. 这样的矩阵与对角阵只有一个 1 的区别，在命题过程中经常出现.

完整的标准型理论比较复杂.本期视频在考研数学范围内来解释若尔当标准型在相似理论中起怎样的作用以及所涉考查方法.

---

![](https://img.hwenyi.live/202410151737717.webp)

若能按照 “$\sim$” 这种相似关系进行分类，每一类里面两个个体都有这种关系，来自不同类的个体不具有这种关系。则这种关系需要满足以下三点：

1. 自反性 $A \sim A$
2. 对称性 若 $A \sim B$，则 $B \sim A$
3. 传递性 若 $A \sim B$，$B \sim C$，则 $A \sim C$

满足三种关系即可称之为等价关系，按照等价关系分的类叫做等价类。矩阵的相似关系就是等价关系.

---

![](https://img.hwenyi.live/202410151717799.webp)

可对角化的矩阵可以找对角阵作为代表元，不可对角化的矩阵只能找若尔当标准型作为代表元.

可对角化充要条件是存在 $n$ 个线性无关的特征向量（任意特征值重数=个数）

最容易考察的考点：

不可对角化充要条件是线性无关的特征向量个数小于 $n$（存在某个特征值的几何重数小于代数重数）

分类策略：以下结论适用于三阶及以下矩阵，或所有特征值的代数重数小于等于 3 的情况。其它情况或许可用也或许不可用.

$n$ 阶矩阵
$$
\begin{cases} 
\text{类1} \\ 
\text{类2} \\ 
\dots 
\end{cases} 
\begin{cases} 
\text{可对角化} (\text{找对角阵}) \\ 
\text{不可对角化} (\text{找若尔当标准型}) 
\end{cases} 
\quad
\begin{pmatrix} 
\lambda_1 & 1 & \\ 
& \lambda_1 & \\ 
& & \lambda_1 
\end{pmatrix}
$$
主对角线上补了几个1就意味着缺几个特征向量

---

![](https://img.hwenyi.live/202410151738573.webp)

矩阵相似，无论能否对角化，只要看它们有没有相同的对角矩阵或若尔当标准型，而对角矩阵/若尔当标准型的形状完全由特征值、特征值的重数以及线性无关的特征向量的个数所决定.

故：两矩阵相似充要于特征值相同；特征值的重数相同；对应线性无关的特征向量的个数相同.

**别忘了下面这个！！！**

**结论适用于三阶及以下矩阵，或所有特征值的重数小于等于 3 的情况。其它情况或许可用也或许不可用.**

---

![](https://img.hwenyi.live/202410151725082.webp)

**总结：**

在阶数 3 阶及以下矩阵或所有特征值的重数小于等于 3 的情况下，若存在某个特征值对应的线性无关的特征向量的个数小于其重数，则该矩阵不可对角化. 且必存在一个与之相似的若尔当标准型.

将特征值排布在对角线上（相同的特征值放在一起），若某个特征值的几何重数比其代数重数少 $k$ 个，就在对应特征值所在对角线的上方或下方**随便**补 $k$ 个 1.

---

![](https://img.hwenyi.live/202410151727538.webp)

下列矩阵中，与矩阵$\begin{pmatrix}1&1&0\\0&1&1\\0&0&1\end{pmatrix}$相似的为

$$(A)\begin{pmatrix}1&1&-1\\0&1&1\\0&0&1\end{pmatrix}.$$

$$(B)\begin{pmatrix}1&0&-1\\0&1&1\\0&0&1\end{pmatrix}.$$

$$(C)\begin{pmatrix}1&1&-1\\0&1&0\\0&0&1\end{pmatrix}.$$

$$(D)\begin{pmatrix}1&0&-1\\0&1&0\\0&0&1\end{pmatrix}.$$

$\lambda = 1$ 三重

$r(E - A) \ne 0$ 只有一个线性无关的特征向量

$r(E - A) = 2 = r(A - E)$

[划掉对角线看秩](https://www.bilibili.com/video/BV18L2dYPEZU?t=592.2)

**所以答案为 A**

---

![](https://img.hwenyi.live/202410151738627.webp)

2 阶若尔当型求解相似矩阵——直接设矩阵即可

**P63 例 3. 20** 若 $A = \begin{bmatrix} 1 & -2 \\ 0 & 1 \end{bmatrix}$, $B = \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}$，求所有可逆矩阵 $P$，使得 $P^{-1}AP = B$.

**解：** 设 $P = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$，则由 $P^{-1}AP = B$ 可得 $AP = PB$，即

$$
\begin{bmatrix} 1 & -2 \\ 0 & 1 \end{bmatrix} \begin{bmatrix} a & b \\ c & d \end{bmatrix} = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \begin{bmatrix} 1 & 1 \\ 0 & 1 \end{bmatrix}
$$

计算可得：

$$
\begin{bmatrix} a - 2c & b - 2d \\ c & d \end{bmatrix} = \begin{bmatrix} a & a + b \\ c & c + d \end{bmatrix}
$$

故：
$$
\begin{cases}
c = 0 \\
a + b = b - 2d
\end{cases}
\Rightarrow
\begin{cases}
c = 0 \\
a = -2d
\end{cases}
$$

$b$ 任意.


---


![](https://img.hwenyi.live/202410151736645.webp)


3 阶若尔当型求解相似矩阵——设矩阵的列

**21. (本题满分 12 分)**
设矩阵 $A = \begin{bmatrix} a & 0 & -2 \\ 1 & a & -1 \\ -1 & -1 & a \end{bmatrix}$, $B = \begin{bmatrix} a - 1 & 1 & 0 \\ 0 & a - 1 & 0 \\ 0 & 0 & a + 2 \end{bmatrix}$.

(1) $A$ 能否相似对角化?说明理由:
(2) 是否存在可逆矩阵 $P$，使得 $P^{-1}AP = B$?若存在，求出所有的 $P$. 若不存在，请说明理由.

**解：**

设 $P = (\xi_1, \xi_2, \xi_3)$，则由 $P^{-1}AP = B$ 可得 $AP = PB$，即

$$
A \begin{bmatrix} \xi_1 & \xi_2 & \xi_3 \end{bmatrix} = \begin{bmatrix} \xi_1 & \xi_2 & \xi_3 \end{bmatrix} \begin{bmatrix} a - 1 & 1 & 0 \\ 0 & a - 1 & 0 \\ 0 & 0 & a + 2 \end{bmatrix}
$$

计算可得：

$$
\begin{cases}
A\xi_1 = (a - 1)\xi_1 \\
A\xi_2 = \xi_1 + (a - 1)\xi_2 \\
A\xi_3 = (a + 2)\xi_3
\end{cases}
$$

$\lambda_A = a + 1, a - 1, a + 2$，但 $a - 1$ 对应的线性无关的特征向量只有一个，所以 $A$ 不能相似对角化.

设 $\xi_1$，则

$$
\begin{aligned}
(A - (a - 1)E)\xi_2 &= \xi_1 \\
\xi_2 &= k_2(2, -1, 1)^T + (2k_1, -3k_1, 0)
\end{aligned}
$$

$$
\begin{cases}
[(a - 1)E - A]{x} = {0} & \Rightarrow \xi_1 = k_1(2, -1, 1)^T \\
[(a + 2)E - A]{x} = {0} & \Rightarrow \xi_3 = k_2(1, 1, 1)^T
\end{cases}
$$

由于 $P$ 可逆，所以 $|P| \ne 0$，即 $k_1 k_2 \ne 0$.

