---
publish: true
tags: []
aliases:
  - 西尔维斯特定理
finished: true
TARGET DECK: 大学数学::线代张宇::第二讲矩阵::矩阵::矩阵方程::可交换矩阵AB=BA
title: 可交换矩阵AB=BA
created: "2024-10-14 10:44"
updated: "2024-10-23 11:14"
---
https://www.bilibili.com/video/BV1fH4y1f7bR?t=4.9

[[第8讲相似理论|o-e9a6]]

AB可交换，==AB都==可以做[[相似对角化]]，而且是同一个[[逆矩阵|可逆矩阵]]P的作用下实现的，在[[刷题/张宇线代强化/第 8 讲相似理论/例8.13]]中证明了它，在[[刷题/张宇线代强化/第 8 讲相似理论/例8.12]]中运用了
<!--ID: 1729417001638-->

Q:AB的[[矩阵乘法]]，可以写成他们的线性组合，那么
A:AB可交换前后顺序$AB=BA$
<!--ID: 1729059064481-->

结论1：无论可变换与否，$A$和$B$为方阵时，$AB$与$BA$有==相同[[特征值]]。==
<!--ID: 1729059064495-->

Q:下面称作西尔维斯特定理
结论2：更进一步，若$A_{m\times n}B_{m\times n}(m\leq n)$有：
$\left|\lambda E_n-AB\right|=\lambda^{n-m}\left|\lambda E_m-BA\right|(\lambda\neq0)$
A:$\lambda^nf_{BA}(\lambda)=\lambda^nf_{AB}(\lambda)$
当 $m=n$ 时，得到更特殊的结论1。
定理的证明是显然的，注意到：
$$\begin{pmatrix}\lambda E_n-BA\\A&\lambda E_m\end{pmatrix}\begin{pmatrix}E_n&-B\\E_m\end{pmatrix}=\begin{pmatrix}\lambda E_n-BA&BAB-\lambda B\\A&\lambda E_m-AB\end{pmatrix}=\begin{pmatrix}E_n&-B\\0&E_m\end{pmatrix}\begin{pmatrix}\lambda E_n\\A&\lambda E_m-AB\end{pmatrix}$$
两侧取[[行列式]]，定理得证。
<!--ID: 1729059064487-->

Q:能够得到矩阵可交换的常用条件：
![](https://img.hwenyi.live/202410151054796.webp)
$AB$ 为方阵情况如下，AB的乘积可以写成线性组合的形式：
A:存在不为 $0$ 的 $\alpha$ 与 $\beta$，$AB = \alpha A + \beta B$ ⇒ $AB = BA$
$AB - \underline{\alpha A - \beta B + \alpha \beta E} = \alpha \beta E$ 
$= \underline{(A - \beta E)(B - \alpha E)} = BA - \alpha A - \beta B + \alpha \beta E$.
上面这个条件A和B可以分解开组合起来，可以得到AB是可交换的，但是反过来，由可交换是不能得到AB可以拆开的这个条件的
<!--ID: 1728996984155-->

Q:可交换矩阵的[[特征值]]、[[特征向量]]关系
A、B为n阶方阵，且AB=BA，则有：
A:(注：1需要掌握，2、3可作为拓展视情况而定)
1. **A与B存在公共特征向量，注意，只是说有相同的，不是全都是一样的**
2. 对A的任一$\lambda$，存在A对应于λ的特征向量x，和B的特征值μ，使得$\lambda\mu$为AB的特征值，且x为B对应于μ，AB对应于λμ的特征向量
3. 对AB的任一$\lambda$，存在AB对应于λ的特征向量x，和A的特征值λ1，B的特征值λ2，使得x为A对应于λ1，B对应于λ2的特征向量，且$\lambda=\lambda1\lambda2$
<!--ID: 1728996984162-->

Q:习题 1：设 $A$，$B$ 均为 $n$ 阶方阵，$A$ 有 $n$ 个不同特征值，则 $AB = BA$ 充要于 $A$ 与 $B$ 特征向量相同
A:我们要证明的是：**如果 $A$ 有 $n$ 个不同特征值，那么 $AB=BA$ 等价于 $A$ 和 $B$ 有相同的特征向量。**
**(1) 必要性：$AB = BA \Rightarrow A$ 与 $B$ 特征向量相同。** 
(2) 充分性：$A$ 与 $B$ 特征向量相同 $\Rightarrow AB = BA$ 
**3. 分步推理:**
**(1) 必要性：**
- **假设：** $AB=BA$， $A$ 有 $n$ 个不同特征值。
- **目标：** 证明 $A$ 和 $B$ 有相同的特征向量。
- **推理过程:**
    1. 设 $\lambda$ 是 $A$ 的任意一个特征值，$\mathbf{x}$ 是 $\lambda$ 对应的特征向量，即 $A\mathbf{x} = \lambda \mathbf{x}$。
    2. 对等式两边左乘 $B$，得到 $BA\mathbf{x} = B(\lambda \mathbf{x}) =  \lambda B\mathbf{x}$。
    3. 由于 $AB=BA$, 所以 $\lambda B\mathbf{x} = AB\mathbf{x}$。
    4. 因此，我们有 $AB\mathbf{x} =  \lambda B\mathbf{x}$，这意味着 $B\mathbf{x}$ 也是 $A$ 对应于特征值 $\lambda$ 的特征向量。
    5. **由于 $A$ 有 $n$ 个不同的特征值**，每个特征值对应**唯一一个**[[线性相关的判定|线性无关]]的特征向量。**因此，$B\mathbf{x}$ 必定与 $\mathbf{x}$ 线性相关**，也就是说，存在一个常数 $k$，使得 $B\mathbf{x} = k\mathbf{x}$。 
    6. 这意味着 $\mathbf{x}$ 也是 $B$ 的特征向量。
    7. 由于 $\lambda$ 是 $A$ 的任意特征值，因此 $A$ 的所有特征向量都是 $B$ 的特征向量。  
**(2) 充分性:**
- **假设：** $A$ 与 $B$ 有相同的特征向量。
- **目标：** 证明 $AB = BA$。
- **推理过程：**
    1. 由于 $A$ 有 $n$ 个线性无关的特征向量，我们可以找到一个由这些特征向量组成的可逆矩阵 $P$，使得 $A$ 可以被对角化，即 $A=P \Lambda_1 P^{-1}$，其中 $\Lambda_1$ 是一个对角矩阵，其对角线元素为 $A$ 的特征值。
    2. 由于 $B$ 与 $A$ 有相同的特征向量，所以 $B$ 也可以被同一个可逆矩阵 $P$ 对角化，即 $B=P \Lambda_2 P^{-1}$，其中 $\Lambda_2$ 是一个对角矩阵，其对角线元素为 $B$ 的特征值。 
    3. 现在，我们可以计算 $AB$ 和 $BA$：
        - $AB = (P\Lambda_1 P^{-1})(P\Lambda_2 P^{-1}) = P \Lambda_1 \Lambda_2 P^{-1}$
        - $BA = (P\Lambda_2 P^{-1})(P\Lambda_1 P^{-1}) = P \Lambda_2 \Lambda_1 P^{-1}$
    4. 由于对角矩阵的乘法满足交换律，所以 $\Lambda_1 \Lambda_2 = \Lambda_2 \Lambda_1$。
    5. 因此，我们得到 $AB = BA$。
![](https://img.hwenyi.live/202410151121419.webp)
<!--ID: 1728996984166-->

习题 2: 设 $A$, $B$ 均为n阶方阵，$A$ 可逆，有：
$$ABA^* = 2BA^{-1} + E$$
1. 证明: $AB=BA$
2. 证明: $A$ 与 $B$ 有相同的特征值
3. $A$ 与 $B$ 是否相似? 
$Bβ = λβ$ 证明 $A$
$|A|AB = 2B + A$ ⇒ $|A|(A-2E)(|A|B-E) = 2E$
$|A|λAβ = 2λ\beta + A\beta$
$(\lambda|A| - 1)A\beta = 2λ\beta$
判断左边的系数不为0，除到右边来就得到了定义的形式
![](https://img.hwenyi.live/202410151143626.webp)
![](https://s3.tebi.io/teyi/202410151143873.webp)

